FROM node:16-alpine

ARG UID=10000
ARG GID=10000
ARG USER_NAME=vscode

# Install packages & set timezone
RUN apk --update --no-cache add \
  git \
  openssh \
  tzdata \
  && cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
  && apk del tzdata \
  && echo "Asia/Tokyo" >  /etc/timezone

# Set locale
ENV LANG=ja_JP.UTF-8
ENV LANGUAGE=ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8

# Switch to non-root user
RUN addgroup -g "${GID}" "${USER_NAME}" \
  && adduser -D -s /bin/ash -u "${UID}" -G "${USER_NAME}" "${USER_NAME}"

USER ${USER_NAME}

# Create workspace
WORKDIR /app