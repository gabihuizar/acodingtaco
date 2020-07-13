---
layout: post
title: How to Make Your Rails App Render a Different Home Page When User Is Not Signed
  In
date: 2016-06-03 22:12:30.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Ruby on Rails
tags:
- coding
- css
- rails
- rubyonrails
meta:
  _edit_last: '1'
  _thumbnail_id: '104'
  _wpas_done_all: '1'
  classic-editor-remember: block-editor
author:
  login: acodingtaco
  email: gaby@acodingtaco.com
  display_name: acodingtaco
  first_name: ''
  last_name: ''
permalink: "/2016/06/03/how-to-make-your-rails-app-render-a-different-home-page-when-user-is-not-signed-in/"
---
This is a problem I encountered when working on [TravelThots](http://travelthots.herokuapp.com), my current passion project. Just as background, the main model of my app is "place", and users can share places they've traveled to. I describe it as a travel version of Instagram; Instead of square photos, you get a feed of square Google maps.

I wanted people to see a different home page when they are not signed in, and wanted them to see the usual "index.html.erb" page that renders all of our "places" when the user is signed in. After reading over the ["Layouts & Rendering" section of RailsGuides](http://guides.rubyonrails.org/layouts_and_rendering.html), I learned that to get your app to render something other than the default layout (application.html.erb), you must go into the controller, and&nbsp;add the following code:

```
class PagesController \< ApplicationController def index render layout: false end end
```

I didn't add this to my main "places" controller, but to a new "pages" controller where all other pages such as about and homepage will be. This will stop the default layout & stylesheet from rendering for the "pages" index.html.erb.

Now in routes.rb, you have to specify which index page you want the user to be shown whether or not they're signed in. In my case, I want signed in users to see places#index, and signed out users to see pages#index.

```
authenticated :user do root 'places#index', as: :authenticated\_root end root "pages#index"
```

You're going to see that your previous CSS is not applied to this new index page. So, in your index.html.erb(pages), you must specify a different stylesheet like so:

```
\<!DOCTYPE html\> \<html\> \<head\> \<title\>TravelThots\</title\> \<meta name="viewport" content="width=device-width, initial-scale=1.0"\> \<%= stylesheet\_link\_tag 'pages' , media: 'all', 'data-turbolinks-track' =\> true %\> \</head\>
```

This is because we want to create brand new style just for this landing page. If you didn't add this stylesheet code, you'd be left with caveman style on your app, like this:

[![caveman CSS]({{ site.baseurl }}/assets/images/Screen-Shot-2016-06-03-at-3.46.20-PM-1024x606.png)](http://acodingtaco.com/wp-content/uploads/2016/06/Screen-Shot-2016-06-03-at-3.46.20-PM.png)

In config/initializers/assets.rb, you have to add this line of code in order for you to&nbsp;precompile the pages stylesheet:

```
Rails.application.config.assets.precompile += %w( pages.css )
```

In Rails, only application.css.scss is precompiled by default so when you add a different stylesheet\_link\_tag in your HTML page, you must add this line of code to assets.rb or your new stylesheet will raise this "asset filter" error:

[![asset filter error]({{ site.baseurl }}/assets/images/Screen-Shot-2016-06-03-at-3.48.39-PM-1024x287.png)](http://acodingtaco.com/wp-content/uploads/2016/06/Screen-Shot-2016-06-03-at-3.48.39-PM.png)

One last thing which only applies if you are using Bootstrap on your app. You must include Bootstrap in your new stylesheet:

```
// Place all the styles related to the Pages controller here. // They will automatically be included in application.css. // You can use Sass (SCSS) here: http://sass-lang.com/ @import "bootstrap-sprockets"; @import "bootstrap";
```

Because you are not using your master stylesheet for this homepage, the Bootstrap that was included in all other stylesheets is not included in your new stylesheet.

If you followed along, you should be left with a nice landing page for people that are aren't signed in or signed up yet.

Good luck!

<!-- wp:paragraph -->

<!-- /wp:paragraph -->

