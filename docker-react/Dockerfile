FROM public.ecr.aws/docker/library/node:16.16.0-alpine3.16 as deps

WORKDIR /tmp
COPY package.json ./
COPY nginx.conf ./




FROM public.ecr.aws/docker/library/node:16.16.0-alpine3.16 as builder


WORKDIR /usr/src/app
COPY --from=deps /tmp/package.json ./
COPY yarn.lock ./

RUN yarn install --production --ignore-scripts --prefer-offline

COPY src/ /usr/src/app/src/
COPY public/ /usr/src/app/public/

RUN yarn build

FROM nginx:stable-alpine

COPY --from=builder /usr/src/app/build /usr/share/nginx/html
COPY --from=deps /tmp/nginx.conf /etc/nginx/nginx.conf

# Clean src
RUN true \
  && rm -rf /usr/src/app

