# BlogApp

First, we're going to talk about how to navigate a user around our app. Real javascript applications allow users to navigate around to see different pages of content. We need to figure out a way to add different pages to our application that the user can see. Second,  we need to figure out how to load data from a back end API based on the users current route. So let say a user navigate around an app to some different page, we need to go and fetch the relevant data before we can render that page. Finally, we need to figure out how to build useful forms that include at least a touch of validation.

# App Details

We're going to be building a simple blogging application. Its going to have the usual create, replace, update, destroy type routes. The first screen will be considered the index in which it'll show all the different blog posts the user currently has. If they click on a blog post, it would navigate them to what's called a "show page" which displays the blog post content. It shows distinctly different view to the user.

The user can also create new posts by clicking the "ADD" post button on the index screen which will take them to kind of a compose form where they'll create a new record or new blog post. The user can enter title categories for the blog pot and the actual content for the blog post. Once they click the save button, it will save the record to a back-end server and then it will navigate them back to the index page. They can also click the cancel button just as easily and go back to the index page as well.

# Posts API

One of the core aspects of this app is the ability to save and then later retrieve blog posts. Lets figure out how we're going to save these blog posts to some remote API. When a user visits our page, they're going to load up our react-redux application in the web browser. The instant that the application loads up inside their browser, we want to show the user a list of blog posts. So presumably, we're going to have to somehow source of find a list of blog posts to show to the user. To store the blog posts, we're going to make use of an API so our application will make an AJAX request to that API and then fetch a list of posts to show to the user on screen.

If we go on "https://reduxblog.herokuapp.com/", it'll take us to a page where Heroku has posted 4 API routes for different purposes in which we can implement into our app. One for fetching all of the blog posts a user has made, posting a blog post, fetching a very particular blog post, and then deleting a blog post.

# React Router

A regular web browser a few years back would work in the following way: a user clicks on a link, it traditionally submits a new request for some new web page from some remote server. The user might click on a link that goes to google.com and it reaches out to google.com, grabs some HTML document from some server and that document is sent back to the users browser where the HTML document appears on the screen. React Routers purpose is to circumvent that process. We are no longer making request to our server to get a web page receiving a web page back and then showing that page to the user, instead React-Router intercepts changes to the URL. When a user clicks on a link, it says "oh I see the user is trying to navigate to a different URL. I'm going to stop that user from navigating to a different page and instead I'm going to manually look at the URL and decide to display a different set of component on the screen based on what that URL is".

When a user clicks on a link or maybe a button that says "create new post", the browser says to the History library "hey, the user just changed the URL. Here's the new the URL or they're trying to visit". The History library takes that new change to the URL. It does some parsing over it and figures out exactly what changed about the URL and then it passes it on to the React-Router library. React-Router receives the new route and its going to decide to show a new set of components on the screen based on exactly what that new route is. Our place in this whole process is to setup that configuration inside React-Router. So we're going to be writing the code that says "hey react-router, if the URL looks like this, then I want you to show this component". Once React-Router has decided what set of component it would like to display based on the URL, its going to say "hey react, it looks like we've got a new set of component to show on the screen please. Please re-render yourself or render all the components that are visible based on this new set of components". In the end, its renders them as content. This is the architecture behind single-page applications (SPA's). The idea behind a SPA is that we're no longer navigating between distinct HTML documents that are being created by some remote web server. Instead we're always dealing with a single HTML document and we're relying upon some javascript to change the et of components that a user sees appearing on the screen.

# Basics of React-Router

We're going to import a couple of things from react-router-dom such as the BrowserRouter. This object interacts with the History library and decides exactly what to do based on a change inside the URL. The term BrowserRouter in particular is saying I want React-Router to look at the entire URL when deciding what different components to show on the screen. The purpose of the RouteComponent is to provide the configuration that will say "hey if the URL looks like this, then I want you show this component and so on." So again, the route object or the route component is all about providing some customization or configuration to react-router.

# Lodash Library

Something we're trying to do is when retrieving the list of posts, the API returns it in the form of a list of objects within an array. However, what we want to do is actually format the posts in the key-value format. For example:

The array of posts can look something like this:

  *const posts = [
    { id: 4, title: "Hey" },
    { id: 25, title: "Bye" },
    { id: 36, title: "How's it going" }
  ];*

However, we want the id of the post to be key that we call upon in which it would display its value (the content of the post), something like this:

  *{
    "4":{"id":4,"title":"Hi"},
    "25":{"id":25,"title":"bye"},
    "36":{"id":36,"title":"Hows it going?"}
   }*

We want the posts to be stored as a list of objects embedded within an object with that specific key value format. In order to do this, we'll use the Lodash javascript library.

We'll use a special method from that library below:

   *_.mapKeys(posts, "id")*

As you can see, we init the lodash library using the underscore and (dot) and used the mapKey method in which we put "posts" as the array parameter we want to work with and the second parameter being "id". What this does is exactly format the list of objects in the way we want. It would end up displaying the array of posts into this list of objects where each id is the key for each post (value).

Now what we can do is create a const called state and assign the mapKey method with our parameters to it:

  *const state = _.mapKeys(posts, "id");*

And we can call that const and input which post we want in particular:

  *state["4"];*

Outputting:

  *"4":{"id":4,"title":"Hi"}*
