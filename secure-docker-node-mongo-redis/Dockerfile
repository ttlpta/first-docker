FROM node:12.18-alpine

WORKDIR /app

COPY . .

RUN npm install

RUN npm install -g pm2

# Create a group and user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

RUN chown -R appuser:appgroup /app

# Tell docker that all future commands should run as the appuser user
USER appuser

CMD ["pm2-runtime", "ecosystem.config.js", "--env", "production"]
