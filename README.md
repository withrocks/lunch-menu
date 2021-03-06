lunch-parser
============

Parser for the menus of the restaurants near Campus Solna of Karolinska Institutet and BMC of Uppsala University.

## Installing

In a python3+ environment, run:

```
pip install -e .
```

## Using the python backend

Usage:

```
lunch-menu restaurant_name > index.html
```

The supported restaurants are also listed when you run main.py without any arguments.

If new restaurants are added, add the parser function to `parser.py`, the relevant keyword and function name to `MAPPER` in `main.py`, and URLs etc to `restaurants.txt`.

It can be run via flask (`FLASK_APP=flask_app.py flask run`).

## Supported endpoints in the flask application:

- `/restaurants` (json): List all supported restaurants
- `/restaurant/<identifier>` (json): Retrieve menu for a restaurant (identifier can be obtained from the above request).
- `/ki` (html): Menu page for restaurants in Solna (KI)
- `/uu` (html): Menu page for restaurants in Uppsala (BMC)

## Hosted versions:

- [Flask app](http://scilifelab-lunches.herokuapp.com/)
- [Vue frontend](http://talavis.eu/menu/)

## Containers:

- [Backend](https://hub.docker.com/repository/docker/scilifelabdatacentre/menu-backend)
- [Frontend hosted in nginx](https://hub.docker.com/repository/docker/scilifelabdatacentre/menu-frontend)

## Slack integration:

Set up an incoming webhook for Slack:

https://slack.com/intl/en-se/help/articles/115005265063-Incoming-WebHooks-for-Slack

Then run e.g. as a cron job:

```
export LUNCH_MENU_SLACK_WEBHOOK=https://hooks.slack.com/services/A_VERY_SECRET_KEY
lunch-menu --slack-channel food uu
```

## Feedback
Bugs and requests for new restaurants or features should be submitted as issues.
