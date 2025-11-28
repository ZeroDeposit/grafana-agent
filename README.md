# Heroku Buildpack for Grafana Cloud Agent

This is an unofficial Heroku buildpack for deploying
**Grafana Alloy** on Heroku.

The buildpack installs the Alloy binary during the build phase and
makes it available at runtime inside the dyno.

## 📦 Usage

Add this buildpack to your Heroku app:

```bash
heroku buildpacks:add https://github.com/ZeroDeposit/grafana-agent
```

Ensure the code of the app includes a config file in:

```bash
config/config.alloy
```

## ▶️ Running Alloy on Heroku

Add a `Procfile` to your application:

```bash
web: bash bin/start.sh
```

And a `bin/start.sh` script with:

```bash
gunicorn app:app &
bin/alloy run config/config.alloy &
wait -n
```
