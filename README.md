[Rainforest](https://addons.heroku.com/marketplace/rainforest) is an [add-on](http://addons.heroku.com) for providing functionality X.

Adding functionality X to an application provides benefits X, Y and Z. [[Sell the benefits here! Don't skimp - developers have many options these days.]]

Rainforest is accessible via an API and has supported client libraries for [[Java|Ruby|Python|Node.js|Clojure|Scala]]*.

## Provisioning the add-on

Rainforest can be attached to a Heroku application via the  CLI:

> callout
> A list of all plans available can be found [here](https://addons.heroku.com/marketplace/rainforest).

```term
$ heroku addons:add rainforest
-----> Adding rainforest to sharp-mountain-4005... done, v18 (free)
```

Once Rainforest has been added a `ADDON-CONFIG-NAME` setting will be available in the app configuration and will contain the [[variable purpose, i.e. "canonical URL used to access the newly provisioned Rainforest service instance."]]. This can be confirmed using the `heroku config:get` command.

```term
$ heroku config:get ADDON-CONFIG-NAME
http://user:pass@instance.ip/resourceid
```

After installing Rainforest the application should be configured to fully integrate with the add-on.

## Local setup

### Environment setup

[[If running against the add-on service during development is not applicable this section can be omitted]]

After provisioning the add-on it’s necessary to locally replicate the config vars so your development environment can operate against the service.

> callout
> Though less portable it’s also possible to set local environment variables using `export ADDON-CONFIG-NAME=value`.

Use [Foreman](config-vars#local-setup) to configure, run and manage process types specified in your app’s [Procfile](procfile). Foreman reads configuration variables from an .env file. Use the following command to add the ADDON-CONFIG-NAME values retrieved from heroku config to `.env`.

```term
$ heroku config -s | grep ADDON-CONFIG-NAME >> .env
$ more .env
```

> warning
> Credentials and other sensitive configuration values should not be committed to source-control. In Git exclude the .env file with: `echo .env >> .gitignore`.

### Service setup

[[If there is a local executable required (like for the memcache add-on) then include installation instructions. If not, omit entire section]]

Rainforest can be installed for use in a local development  environment.  Typically this entails [[installing the software | creating another version of the service]] and pointing the ADDON-CONFIG-NAME to this [[local | remote]] service.

<table>
  <tr>
    <th>If you have...</th>
    <th>Install with...</th>
  </tr>
  <tr>
    <td>Mac OS X</td>
    <td style="text-align: left"><code>brew install X</code></td>
  </tr>
  <tr>
    <td>Windows</td>
    <td style="text-align: left">Link to some installer</td>
  </tr>
  <tr>
    <td>Ubuntu Linux</td>
    <td style="text-align: left"><code>apt-get install X</code></td>
  </tr>
  <tr>
    <td>Other</td>
    <td style="text-align: left">Link to some raw package</td>
  </tr>
</table>

## Using with Rails 3.x

[[Repeat this ##Rails 3.x sections for all other supported languages/frameworks including Java, Node.js, Python, Scala, Play!, Grails, Clojure. Heroku is a polyglot platform - don't box yourself into supporting a single language]]

Ruby on Rails applications will need to add the following entry into their `Gemfile` specifying the Rainforest client library.

```ruby
gem 'rainforest'
```

Update application dependencies with bundler.

```term
$ bundle install
```

[[Describe briefly how to use/integrate your service from Rails 3.x with code samples]]

## Using with Python/Django

[[Repeat structure from Rails 3.x section]]

## Using with Java, Node....

[[Repeat structure from Rails 3.x section for each supported language]]

## Monitoring & Logging

Stats and the current state of Rainforest can be displayed via the CLI.

```term
$ heroku rainforest:command
example output
```

Rainforest activity can be observed within the Heroku log-stream by [[describe add-on logging recognition, if any]].

```term
$ heroku logs -t | grep 'rainforest pattern'
```

## Dashboard

> callout
> For more information on the features available within the Rainforest dashboard please see the docs at [mysite.com/docs](mysite.com/docs).

The Rainforest dashboard allows you to [[describe dashboard features]].

The dashboard can be accessed via the CLI:

```term
$ heroku addons:open rainforest
Opening rainforest for sharp-mountain-4005…
```

or by visiting the [Heroku apps web interface](http://heroku.com/myapps) and selecting the application in question. Select Rainforest from the Add-ons menu.

## Troubleshooting

If [[feature X]] does not seem to be [[common issue Y]] then 
[[add specific commands to look for symptoms of common issue Y]].

## Migrating between plans

Use the `heroku addons:upgrade` command to migrate to a new plan. Your plan change will be reflected immediately.

```term
$ heroku addons:upgrade rainforest:newplan
-----> Upgrading rainforest:newplan to sharp-mountain-4005... done, v18 ($49/mo)
       Your plan has been updated to: rainforest:newplan
```

## Removing the add-on

Rainforest can be removed via the  CLI.

> warning
> This will destroy all associated account data and cannot be undone!

```term
$ heroku addons:remove rainforest
-----> Removing rainforest from sharp-mountain-4005... done, v20 (free)
```

## Support

All Rainforest support and runtime issues should be submitted via on of the [Heroku Support channels](support-channels).