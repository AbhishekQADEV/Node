FROM node:21-alpine
WORKDIR /usr/src/app
COPY . .
RUN npm install --ignore-scripts --unsafe-perm
EXPOSE 80
CMD [ "npm", "start" ]