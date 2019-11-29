FROM node:latest

ENV APP_ROOT=/app
ENV APP_PORT=3000
ENV DB_HOST=localhost
ENV DB_PORT=3306 
ENV DB_USER=root 
ENV DB_PASSWORD=changeit 

# Create the directory and cd into it
WORKDIR ${APP_ROOT}

# Copy files into the image
# files will be copied into /app
ADD main.js .
ADD package.json .
ADD config config
ADD public public
ADD views views

# Run some commands
RUN npm install

## How an image is provision/run

# What port our container is exposing
EXPOSE ${APP_PORT}


# Add healthcheck to the application
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
    CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

ENTRYPOINT [ "node", "main.js"]

CMD [""]

