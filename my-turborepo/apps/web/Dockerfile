#FROM node:alpine

# https://github.com/hirosystems/explorer/pull/582/commits/045e01f9405d5073a914f53e796dcb0bf66c39e2
FROM node:18-alpine AS deps

# Define an ARG variable passed in as --build-arg
ARG DATABASE_URL

# Use the ARG value in the environment variable (ARG is passed in to docker build command as --build-arg)
# make sure that since this is GitHub Actions building, that it access the remote mysql database
ENV DATABASE_URL=$DATABASE_URL

# Create app directory
RUN mkdir -p /usr/src
WORKDIR /usr/src



# Install app dependencies
COPY package.json /usr/src/
COPY package-lock.json /usr/src/
RUN npm install

# Bundle app source
COPY . /usr/src

# Run Prisma generate
RUN npx prisma generate

RUN npm run build
EXPOSE 3000

CMD ["npm", "start"]