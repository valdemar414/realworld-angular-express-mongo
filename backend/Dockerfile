# Use a smaller base image
FROM node:21-alpine

# Set NODE_ENV to production
ENV NODE_ENV=production

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
COPY package*.json ./

# Use npm ci for a production build
RUN npm ci --only=production

COPY . .
EXPOSE 3000

# Use PM2 to manage the app
RUN npm install pm2 -g
CMD ["pm2-runtime", "start", "npm", "--", "start"]
