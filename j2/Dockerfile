FROM node:20-alpine AS build
WORKDIR /app
COPY /package.json .
RUN npm install

FROM node:20-alpine AS development
USER node
WORKDIR /app
COPY --from=build /app .
CMD [ "npm","run","develop" ]

FROM node:20-alpine AS production
USER node
COPY --from=build /app .
COPY . .
CMD [ "node","index.js" ]