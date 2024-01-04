FROM node:13-alpine

WORKDIR /app

ADD . .

RUN npm install

# Prints out in the entrypoint.sh when starting container
ENTRYPOINT ["sh", "/app/entrypoint.sh"]

CMD ["npm", "start"]