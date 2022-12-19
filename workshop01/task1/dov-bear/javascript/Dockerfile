# Building the image
FROM node:16

LABEL “name”=“myapp-dov-bear”

ADD main.js .
ADD package.json .
ADD public public
ADD views views

RUN npm i

# Running the image
ENV PORT=3000 INSTANCE_NAME="dov-bear" INSTANCE_HASH=""
EXPOSE $PORT

HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD curl -s -f http://localhost:${PORT}/healthz > /dev/null || exit 1

ENTRYPOINT node main.js
CMD [ “$PORT” ]