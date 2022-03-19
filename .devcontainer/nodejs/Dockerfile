FROM node:16-alpine

ARG UID=10000
ARG GID=10000
ARG USER_NAME=minteel

# Install packages & set timezone
RUN apk --update --no-cache add \
  git \
  openssh \
  tzdata \
  && cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
  && apk del tzdata \
  && echo "Asia/Tokyo" > /etc/timezone

# Alpine has no locale, so we don't have to change locale.

# Switch to non-root user
RUN addgroup -g "${GID}" "${USER_NAME}" \
  && adduser -D -s /bin/ash -u "${UID}" -G "${USER_NAME}" "${USER_NAME}"

USER ${USER_NAME}

# Create workspace
WORKDIR /app

RUN mkdir node_modules
