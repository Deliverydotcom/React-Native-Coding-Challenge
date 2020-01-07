# delivery.com React Native Coding Challenge

## 1. Goal

Your goal is to build a react native app that displays a list of restaurants for an inputted address. We will provide guidelines and feature requests below, but ultimately the design and functionality of your app is up to you. Keep in mind functionality and code quality is more important than asthetic design.

## 2. Instructions

Please read through the rest of the requirements and additional info before working on your app.

You can refer to the [getting started guide](https://facebook.github.io/react-native/docs/getting-started) if you need help initilizing a new react native project. We would prefer if you did so **without** using Expo, however the choice is ultimately up to you.

Alternatively, if you do not have an environment in which to work on a React Native app, you can use https://snack.expo.io/.

If you are still having problems please email jsessler@delivery.com.

You can use third party libraries, but the more code you write yourself, the better.

You have 1 week to submit your code, however we want to be respectful of your time and do **not** expect you to work for more than **4 hours** on this challenge.

When you are finished please submit a .zip file with your entire project (node_modules included) to jsessler@delivery.com (or a link to your expo snack project).

## 3. Basic Requirements

 * Your app should have a text input that allows a user to enter an address in the format `"{street address}, {zip code}"`
 * Your app should fetch data on restaurants that deliver to that address, using the delivery.com API (see more below)
 * Your app should display these restaurants as a list, you can include whatever information about each restaurant you would like
 * Your app should run on iOS or Android

## 4. Bonus Features

 These features are **absolutely not** required, however if you finish your project early and wish to continue here are some ideas:
  * Implement "pull to refresh" on the list
  * Implement validation on the text input, so users see an error if they attempt to submit a malformatted address
  * Include a "share" button on each search result that allows you to send a link to the restaurants home page to a friend using the share dialog
  * Keep a history of previous address searches (double bonus if it persists between app launches)

## 5. Using the delivery.com API

You will be using a spoofed version of the delivery.com search API to fetch a list of restaurants. The URL looks like:

```
https://dcom-native-interview.s3.amazonaws.com/api/merchant/query/:address
```

Please use the address from the text input, remove any non-digit characters, and convert it to lowercased camel_case.

For example if a user types in "55 Water St, 10041" your GET request should look like this:

```
fetch('https://dcom-native-interview.s3.amazonaws.com/api/merchant/query/55_water_st_10041');
```

For simplicity please only use the following addresses:

 * 55 Water St, 10041
 * 240 Kent Ave, 11249
 * 232 Willow Ave, 07030
 * 245 E 63rd St, 10065

You can expect a json response that will contain a key called `merchants` with an array of merchant objects that look like:

```
{
  "id": number,
  "name": string,
  "logo_url": string,
  "url": {
      "complete": string
  },
  "ratings": {
      "overall_rating": number, // out of 100
      "star_rating": number, // out of 5 stars
      "num_ratings": number
  },
  "cuisines": string[],
  "price_rating": number, // out of 4
  "location": {
      "street": string,
      "state": string,
      "zip": string
  }
}
```
