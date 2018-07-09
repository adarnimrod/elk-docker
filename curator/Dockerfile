FROM python:3.7-alpine
RUN pip install --progress-bar=off --no-cache-dir elasticsearch-curator==5.5.4
COPY --chown=root:root entrypoint /
ENTRYPOINT [ "/entrypoint" ]
CMD [ "/usr/sbin/crond", "-fd7" ]
HEALTHCHECK --timeout=1s CMD pgrep crond || exit 1
