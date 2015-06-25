![gulp-ink-sass email](https://cloud.githubusercontent.com/assets/3684236/8302244/d8a6a230-1949-11e5-9e38-22bd1164c9be.png)
### Gulp Ink Scss Email Workflow
---
Designing and testing email templates are pain. This workflow makes email template design and testing a piece of cake.
  * Design email template using [Sassy Ink](https://github.com/faustgertz/sassy-ink).
  * Automate build process using [Gulp](http://gulpjs.com/).
  * Compile SCSS to CSS and inline them using [Premailer](#).
  * Layouts and Partials to streamline the development process using [Handlebars](http://handlebarsjs.com/).
  * Auto upload images to AWS S3 and replace `img` tags.
  * Configure [Sendgrid](https://sendgrid.com/), [Mandrill](http://mandrillapp.com), or [Mailgun](http://www.mailgun.com/) to send test emails.
  * Congigure [Litmus](https://litmus.com/) for testing emails.

#### Install Node & Gulp

    * Nodejs             $ brew install node
    * Gulp               $ npm install --global gulp

#### Install Ruby & Dependancies

    * Rbenv       $ brew install/upgrade rbenv
    * Ruby Build  $ brew install/upgrade ruby-build
    * Ruby        $ rbenv install 2.2.2
    * Premailer   $ gem install premailer hpricot nokogiri

#### Clone and install dependancies

    $ git clone git@github.com:dahal/inky.git
    $ mv inky YOUR_PROJECT_NAME
    $ cd YOUR_PROJECT_NAME
    $ npm install

#### `secrets.json` file
> Rename `example.secrets.json` to `secrets.json` and update the settings

    {
      "mandrill": {
        "api_key": "YOUR_API_KEY",
        "sender": "SENDER_EMAIL",
        "recipient": "YOUR EMAIL HERE"
      },
      "sendgrid": {
        "api_key": "YOUR_API_KEY",
        "sender": "SENDER_EMAIL",
        "recipient": "YOUR EMAIL HERE"
      },
      "mailgun": {
        "api_key": "YOUR_API_KEY",
        "sender": "SENDER_EMAIL",
        "recipient": "YOUR EMAIL HERE"
      },
      "s3": {
        "key": "YOUR_API_KEY",
        "secret": "YOUR_API_SECRED",
        "bucket": "YOUR_S3_BUCKET",
        "directory": "S3_DIRECTORY",
        "base_url": "https://s3.amazonaws.com"
      },
      "litmus": {
        "username": "LITMUS_USER_NAME",
        "password": "LITMUS_PASSWORD",
        "company": "COMPANY_NAME"
      }
    }

#### Frequently Used Gulp Tasks

    $ gulp                                  # Compile partials, layout, scss and build inlined template.
    $ gulp upload                           # Upload local images to s3 and replace them on html file.
    $ gulp email --template=welcome.html    # Send compiled template to yourself for test.
