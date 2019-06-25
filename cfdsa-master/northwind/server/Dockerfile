
## for docker build

FROM node:latest

#env 
ENV DB_HOST=nwdb DB_PORT=3306 \
    DB_USER=root DB_PASSWORD=changeit \
    APP_PORT=3000 APP_DIR=/app

#create APP_DIR, and cd inside
WORKDIR ${APP_DIR}

#copy files to APP_DIR
ADD main.js .
#file can put .
ADD package.json .

#directory must specify target name 
ADD public public 
ADD views views
ADD config config

#install library form package.json
RUN npm install


## for docker run

EXPOSE ${APP_PORT}

#integrate health check into docker
HEALTHCHECK --interval=60s --timeout=5s  \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1


#how should the image be executed
ENTRYPOINT ["node", "main.js"]

#CMD ["${APP_PORT}"]