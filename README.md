brunch-nginx
==================

You don't need to use node to serve a brunch site - you can just build the files and use anything - `brunch build`

This is a container that has node and brunch available, to compile and install the static site, that nginx serves.

You can use our container: `docker pull xorcode/brunch-nginx`

Or you can build your own:

```
docker build -t your-name-here/brunch-nginx .
docker push your-name-here/brunch-nginx
```

After this - just add this Dockerfile to your Brunch repo:

```
FROM xorcode/brunch-nginx

WORKDIR /srv/www

ADD . /srv/www/
RUN harp compile

EXPOSE 80

CMD nginx
```

Push it to your docker server - and your server will use 4-6MB of RAM instead of 60MB.
