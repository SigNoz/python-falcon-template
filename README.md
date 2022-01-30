# python-falcon-template
A sample template for Python Falcon API application.



## Install application dependencies
```
pip3 install -r requirements/base.txt
```
```
opentelemetry-bootstrap --action=install
```

#### Install Redis server
For Mac
```
brew install redis
brew services start redis
```

For Ubuntu
```
sudo apt install redis-server
```

## How to run server
```
gunicorn -b 0.0.0.0:8001 --reload src.app
```

## Run with instrumentation SigNoz
```
OTEL_RESOURCE_ATTRIBUTES=service.name=flaconApp OTEL_EXPORTER_OTLP_ENDPOINT="<IP of SigNoz>:4317" opentelemetry-instrument gunicorn src.app -b 0.0.0.0:8001
```

## Start browsing application and checkout data at SigNoz's UI
Visit `http://localhost:8001/api/v1/test` which is served by Falcon

and visit SigNoz's UI to checkout application performance
