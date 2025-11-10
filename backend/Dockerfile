# backend/Dockerfile
FROM node:18-alpine AS runtime
WORKDIR /app

# copy only package files for caching
COPY package.json package-lock.json ./

# install only production dependencies
RUN npm ci --omit=dev --silent

# copy only necessary source code
COPY src ./src

# expose backend port
EXPOSE 5001

# run as non-root user for security
USER node

# start backend server
CMD ["node", "src/index.js"]

