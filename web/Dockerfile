FROM node:18 AS Base
CMD [ "bash" ]


#build
FROM Base AS test-and-build
COPY . /workspace
WORKDIR /workspace
ARG REACT_APP_API_SERVER
RUN nmp ci && nmp run test && nmp run build



#Hosting in nginx
FROM nginx:latest AS production
COPY --from=test-and-build /workspace/build /var/www
COPY nginx.conf /etc/nginx/conf.d/default.conf