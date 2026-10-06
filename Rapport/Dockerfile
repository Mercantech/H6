# Produktion: byg statisk MkDocs-site og servér med nginx (Traefik → :80)
FROM python:3.12-slim-bookworm AS build

WORKDIR /app
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

COPY requirements-docs.txt .
RUN pip install --no-cache-dir -r requirements-docs.txt

COPY . .
RUN mkdocs build

FROM nginx:1.27-alpine

COPY nginx.default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/site /usr/share/nginx/html

EXPOSE 3000
