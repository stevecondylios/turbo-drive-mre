# turbo-drive-mre
A simple example of Turbo Drive in a rails app, for reference purposes


From [Hotwire docs](https://turbo.hotwired.dev/):

> Turbo Drive accelerates links and form submissions by negating the need for full page reloads.

- Based on this awesome tutorial: https://www.youtube.com/watch?v=0CSGsHnci2I


### Summary of how turbo streams can be made to work with a basic todo list app 

This summarises how the firs 20 min or so of the (webcrunch hotwire) tutorial works (not the edit functionality, just the form and instant diaply of new items). 

1. Load index.html.erb
2. That will load @todos (which is Todo.all) and display them
3. We edited the index view also display a form partial.
4. The form partial accepts a variable 'todo', and we don't need anything fancy from the controller but can simply pass it Todo.new 
5. The todos displayed on index view are interesting. Simply `render @todos` is enough for rails to figure out it needs to look for a _todo.html.erb and run it for each record in @todos. Neat.
6. When we submit, it creates a POST to todo#create
7. The single line format.turbo_stream is enough for rails to figure out it shouldn't run the html based stuff, but instead simply run the create.turbo_stream.html file instead
8. That turbo code will the thing on the page with dom id "todos" (it's the list of todos) (interestingly it also won't load any pages or redirect)
9. It will add a single thing to it (prepend)
10. That thing is: render "todo", todo: @todo
11. Then, it will refresh the form with a new one. 
12. That's it! 
