FROM node:14.15.1-alpine3.12 as builder
ARG REACT_APP_BASE_URL
ENV REACT_APP_BASE_URL $REACT_APP_BASE_URL
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:1.19.0
EXPOSE 3333
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html