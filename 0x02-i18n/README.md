
# 0x02. i18n

This project focuses on internationalization (i18n) using Flask and Babel. It covers various tasks related to language localization, time zones, and parametrizing templates.

## 0. Basic Flask app

In `0-app.py`, set up a basic Flask app with the following features:
- Create a single `/` route.
- Create an `index.html` template that displays:
  - Page title: "Welcome to Holberton"
  - Header: "Hello world"

## 1. Basic Babel setup

1. Install the Babel Flask extension:
   ```
   $ pip3 install flask_babel==2.0.0
   ```

2. Instantiate the Babel object in your app and store it in a module-level variable named `babel`.

3. Create a `Config` class with a `LANGUAGES` class attribute equal to `["en", "fr"]`.

4. Set Babel’s default locale to `"en"` and timezone to `"UTC"` using the `Config` class as the configuration for your Flask app.

## 2. Get locale from request

Create a `get_locale` function with the `babel.localeselector` decorator. Use `request.accept_languages` to determine the best match with our supported languages.

## 3. Parametrize templates

Use the `_` or `gettext` function to parametrize your templates. Use the message IDs `home_title` and `home_header`.

## 4. Force locale with URL parameter

Implement a way to force a particular locale by passing the `locale=fr` parameter to your app’s URLs.

In your `get_locale` function:
- Detect if the incoming request contains the `locale` argument.
- If its value is a supported locale, return it.
- If not or if the parameter is not present, resort to the previous default behavior.

Now you should be able to test different translations by visiting `http://127.0.0.1:5000?locale=[fr|en]`.

## 5. Mock logging in

To emulate user login behavior, copy the following user table in `5-app.py`:

## 6. Use user locale

Change your `get_locale` function to use a user’s preferred locale if it is supported. The order of priority should be:
1. Locale from URL parameters
2. Locale from user settings
3. Locale from request header

## 7. Infer appropriate time zone

Define a `get_timezone` function and use the `babel.timezoneselector` decorator.

## 8. Display the current time (advanced)

Based on the inferred time zone, display the current time on the home page in the default format.
