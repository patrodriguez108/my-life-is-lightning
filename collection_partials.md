<h1>Collection Partials</h1>

<p>Collection partials are a specific form of partial. They can render partials from within a views folder without needing to specify anything. IT'S RIDICULOUS.</p>

<h3>Basics</h3>

<p>So like let's say in my posts controller, and in my index method I have Post.all set to @posts and I have a partial called _post.html.erb, and it's nested in views/posts. If I wanted to render all of the posts, using the partial from my posts folder in views I can just say something like:</p>


	 
	<%= render partial: "post", collection: @posts %>

	

<p>And it will AUTOMATICALLY FIND THAT PARTIAL WITHOUT ME NEEDING TO DO ANYTHING. I can drink a cup of tea instead of typing that nested route. Thank you Railsy bb.</p>

<p>Even nicer, I don't even need to write all of that. I can just say:</p>


	 
	<%= render @posts %>

	

<p>And it will do the same damn thing. IT'S WILD YO.</p>

<p>If the collection is empty, render will return nil. We have the option in this case to provide a default statement.</p>

	<%= render(@posts) || "Ay there ain't nothin' in dis tho" %>
	
<p>This even works for collections that belong to specific objects. While we could iterate through a collection, like a specific post's comments, and render that partial, like:</p>


	
	<% @post.comments.each do |comment| %>
  		<%= render comment %>
	<% end %>

	
 	
<p>We can instead just say:</p>

	

 	<%= render @post.comments %>

  	

<p>It gets even wilder! Because we can even render a collection of different objects from different collections. These are called heterogeneous collections:</p>

	
 	<%= render @user.favorites %> #--> renders favorite photos, comments, posts

 	<%= render [post1, comment2, comment3, post3, comment5] %>

 	<%= render [@post1, @comment2, @comment3, @post3, @comment5] %>
	
<h3>Behind the Scenes</h3>

<p>How this all works is that when we call on the built in render method, behind the scenes we are calling on a method called "to_partial_path" on EACH of the objects within that collection. So when I say "render @posts", I am also saying:</p>


	
 	@posts.each do |post|
 	   post.to_partial_path
 	end

 	

<p>The method "to_partial_path" finds the partial that matches the model name that defines the object. This works for all models that inherit from ActiveRecord::Base.</p>

<p>Thank you for listening to me. But really it wasn't really hard to learn all this. It was just partial work.</p>

<p><ul>Sources</ul></p>

<p><a href="https://robots.thoughtbot.com/rendering-collections-in-rails">Rendering Collections in Rails</a></p>
<p><a href="http://guides.rubyonrails.org/layouts_and_rendering.html">Rails Guides: Layouts and Rendering in Rails, Section 3.4.5: Rendering Collections</a></p>
