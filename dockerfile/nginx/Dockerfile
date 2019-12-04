FROM nginx:1.17.6-alpine

RUN apk update && \
  apk upgrade --update-cache --available

EXPOSE 80

CMD ["nginx", "-g",  "daemon off;"]
