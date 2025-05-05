Privacy-respecting, hackable [metasearch
engine](https://en.wikipedia.org/wiki/Metasearch_engine)

[Searx.space](https://searx.space) lists ready-to-use running instances.

A [user](https://docs.searxng.org/user),
[admin](https://docs.searxng.org/admin) and
[developer](https://docs.searxng.org/dev) handbook is available on the
[homepage](https://docs.searxng.org/).

## How to use it
There are two ways to host SearXNG. The first one doesn't require any prior knowledge about self-hosting and thus is recommended for beginners. It includes caddy as a reverse proxy and automatically deals with the TLS certificates for you. The second one is recommended for more advanced users that already have their own reverse proxy (e.g. Nginx, HAProxy, ...) and probably some other services running on their machine. The first few steps are the same for both installation methods however.

1. Edit the [.env](https://github.com/searxng/searxng-docker/blob/master/.env) file to set the hostname and an email
2. Generate the secret key `sed -i "s|ultrasecretkey|$(openssl rand -hex 32)|g" searxng/settings.yml`  
   On a Mac: `sed -i '' "s|ultrasecretkey|$(openssl rand -hex 32)|g" searxng/settings.yml`
3. Edit [searxng/settings.yml](https://github.com/searxng/searxng-docker/blob/master/searxng/settings.yml) according to your needs

> [!NOTE]
> On the first run, you must remove `cap_drop: - ALL` from the `docker-compose.yaml` file for the `searxng` service to successfully create `/etc/searxng/uwsgi.ini`. This is necessary because the `cap_drop: - ALL` directive removes all capabilities, including those required for the creation of the `uwsgi.ini` file. After the first run, you should re-add `cap_drop: - ALL` to the `docker-compose.yaml` file for security reasons.