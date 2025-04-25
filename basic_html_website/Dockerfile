# select base image
FROM nginx

# label it (optional)
LABEL MAINTAINER=jamesc830

# copy from local host to container
COPY index.html /usr/share/nginx/html/

# allow required port
EXPOSE 80

# execute required commands
CMD ["nginx", "-g", "daemon off;"]