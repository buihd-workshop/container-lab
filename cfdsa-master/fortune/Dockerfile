FROM node:latest

ENV APP_PORT=5000 APP_DIR=/fortune


## docker build

#create APP_DIR, and cd inside
WORKDIR ${APP_DIR}

#copy files to APP_DIR
ADD main.js .
#file can put .
ADD package.json .

#directory must specify target name 
ADD public public 
ADD views views

#install library form package.json
RUN npm install


## docker run

EXPOSE ${APP_PORT}

#integrate health check into docker
HEALTHCHECK --interval=60s --timeout=5s  \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1


#how should the image be executed
ENTRYPOINT ["node", "main.js"]

#CMD ["${APP_PORT}"]