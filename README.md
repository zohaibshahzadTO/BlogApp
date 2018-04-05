# BlogApp

First, we're going to talk about how to navigate a user around our app. Real javascript applications allow users to navigate around to see different pages of content. We need to figure out a way to add different pages to our application that the user can see. Second,  we need to figure out how to load data from a back end API based on the users current route. So let say a user navigate around an app to some different page, we need to go and fetch the relevant data before we can render that page. Finally, we need to figure out how to build useful forms that include at least a touch of validation.

# App Details

We're going to be building a simple blogging application. Its going to have the usual create, replace, update, destroy type routes. The first screen will be considered the index in which it'll show all the different blog posts the user currently has. If they click on a blog post, it would navigate them to what's called a "show page" which displays the blog post content. It shows distinctly different view to the user.

The user can also create new posts by clicking the "ADD" post button on the index screen which will take them to kind of a compose form where they'll create a new record or new blog post. The user can enter title categories for the blog pot and the actual content for the blog post. Once they click the save button, it will save the record to a back-end server and then it will navigate them back to the index page. They can also click the cancel button just as easily and go back to the index page as well.

# Posts API

One of the core aspects of this app is the ability to save and then later retrieve blog posts. Lets figure out how we're going to save these blog posts to some remote API. When a user visits our page, they're going to load up our react-redux application in the web browser. The instant that the application loads up inside their browser, we want to show the user a list of blog posts. So presumably, we're going to have to somehow source of find a list of blog posts to show to the user. To store the blog posts, we're going to make use of an API so our application will make an AJAX request to that API and then fetch a list of posts to show to the user on screen.

If we go on "https://reduxblog.herokuapp.com/", it'll take us to a page where Heroku has posted 4 API routes for different purposes in which we can implement into our app. One for fetching all of the blog posts a user has made, posting a blog post, fetching a very particular blog post, and then deleting a blog post.
