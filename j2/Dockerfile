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
COPY --from=build /app .
COPY . .
RUN [ "npm","run","build" ]
CMD [ "node","index.js" ]