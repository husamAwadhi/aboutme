# base node image
FROM node:17.5.0-alpine3.15 as base

# Install openssl for Prisma
RUN apk upgrade --update-cache --available && \
    apk add openssl && \
    rm -rf /var/cache/apk/*

WORKDIR /app

ADD package.json package-lock.json ./
RUN npm install --production=false

# If we're using Prisma, uncomment to cache the prisma schema
# ADD prisma .
# RUN npx prisma generate

ADD . .
RUN npm run build_dev
ENV NODE_ENV=production

CMD ["npm", "run", "start_dev"]
