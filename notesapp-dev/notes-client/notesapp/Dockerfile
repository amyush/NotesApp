# Stage 1
FROM node:10.21.0-alpine as node
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2

EXPOSE 4200
CMD ["npm", "start"]
