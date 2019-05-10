FROM adarnimrod/cron as supersonic

FROM python:3.7-alpine3.9
COPY --from=supersonic /usr/local/bin/supersonic /usr/local/bin/
RUN pip install --progress-bar=off --no-cache-dir elasticsearch-curator==5.7.6
USER nobody
CMD [ "supersonic", "/etc/crontabs/nobody" ]
HEALTHCHECK --timeout=1s CMD pgrep supersonic || exit 1
