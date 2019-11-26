FROM node:latest

## How an image is built
# Set environment variables
ENV APP_ROOT=/app
ENV APP_PORT=3000

# Create the directory and cd into it
WORKDIR ${APP_ROOT}

# Copy files into the image
# files will be copied into /app
ADD main.js .
ADD package.json .
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