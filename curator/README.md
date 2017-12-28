# curator-docker

> A dockerized Elasticsearch Curator.

## Usage

This image contains the Elasticsearch Curator but runs a Cron daemon. To use
this image you need to provide your `crontab` and perhaps `config.yml` and
`actions.yml` for Curator.

An example mounting a `crontab` as a volume (every day at 01:00 delete
`logstash-` indices older than 7 days).

```
docker run -v crontab:/var/spool/cron/crontabs/nobody:ro adarnimrod/curator
```

And the accompanying `crontab`

```
0 1 * * * /usr/local/bin/curator_cli --host elastic delete_indices --filter_list '[{"filtertype": "pattern", "kind": "prefix", "value": "logstash-"}, {"filtertype": "age", "source": "creation_date", "direction": "older", "unit": "days", "unit_count": 7}]'
```

Or you can build your own image, using this one as a base

```
FROM adarnimrod/curator
COPY config.yml /etc/curator.yml
COPY actions.yml /actions.yml
COPY crontab /var/spool/cron/crontabs/nobody
```

## License

This software is licensed under the MIT license (see `LICENSE.txt`).

## Author Information

Nimrod Adar, [contact me](mailto:nimrod@shore.co.il) or visit my [website](
https://www.shore.co.il/). Patches are welcome via [`git send-email`](
http://git-scm.com/book/en/v2/Git-Commands-Email). The repository is located
at: <https://www.shore.co.il/git/>.
