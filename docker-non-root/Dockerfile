FROM node:12.18-alpine

WORKDIR /app

RUN npm install -g pm2

COPY ["package.json", "package-lock.json*", "./"]

RUN npm install --production --silent

COPY . .

USER node

# RUN addgroup -g 1410 appgroup
# RUN adduser -D -u 1410 appuser -G appgroup

# #RUN chown -R node:node /app
# RUN chown -R appuser:appgroup /app

# # Tell docker that all future commands should run as the appuser user
# USER appuser

CMD ["pm2-runtime", "ecosystem.config.js", "--env", "production"]