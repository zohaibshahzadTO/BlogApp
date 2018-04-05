# BlogApp

First, we're going to talk about how to navigate a user around our app. Real javascript applications allow users to navigate around to see different pages of content. We need to figure out a way to add different pages to our application that the user can see. Second,  we need to figure out how to load data from a back end API based on the users current route. So let say a user navigate around an app to some different page, we need to go and fetch the relevant data before we can render that page. Finally, we need to figure out how to build useful forms that include at least a touch of validation.

# App Details

We're going to be building a simple blogging application. Its going to have the usual create, replace, update, destroy type routes. The first screen will be considered the index in which it'll show all the different blog posts the user currently has. If they click on a blog post, it would navigate them to what's called a "show page" which displays the blog post content. It shows distinctly different view to the user.

The user can also create new posts by clicking the "ADD" post button on the index screen which will take them to kind of a compose form where they'll create a new record or new blog post. The user can enter title categories for the blog pot and the actual content for the blog post. Once they click the save button, it will save the record to a back-end server and then it will navigate them back to the index page. They can also click the cancel button just as easily and go back to the index page as well.
