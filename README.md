# uwsgi-example-python

Example uWSGI deployment taken from 
https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html

# Prerequisites

pip3 install uwsgi


# Create simple application handler as foobar.py

```
def application(env, start_response):
    start_response('200 OK', [('Content-Type','text/html')])
    return [b"Hello World"]
```

# Deploy using uwsgi

```
uwsgi --http :9090 --wsgi-file foobar.py
```

# Adding concurrency and monitoring

```
uwsgi --http :9090 --wsgi-file foobar.py --master --processes 4 --threads 2
```

# Adding a statistics endpoint

```
uwsgi --http :9090 --wsgi-file foobar.py --master --processes 4 --threads 2
--stats 127.0.0.1:9191
```

# Install and use uwsgitop 

```
pip install uwsgitop
```


# Install gevent support

```
pip install gevent
```


# Execute uwsgi with gevent support

```
uwsgi --gevent 100 --http :3031 --module mygevent
```
