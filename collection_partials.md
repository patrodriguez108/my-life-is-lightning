<h1>Collection Partials</h1>

<p>Collection partials are a specific form of partial. They can render partials from within a views folder without needing to specify anything. IT'S RIDICULOUS.</p>

<p>So like let's say in my users controller, and in my index method I have Users.all set to @users and I have a partial called _user.html.erb, and it's nested in views/users. If I wanted to render all of the users, using the partial from my users folder in views I can just say something like:</p>

	 
	<%= render partial: "user", collection: @users %>

	

<p>And it will AUTOMATICALLY FIND THAT PARTIAL WITHOUT ME NEEDING TO DO ANYTHING. I can drink a cup of tea instead of typing that nested route. Thank you Railsy bb.</p>

<p>Even nicer, I don't even need to write all of that. I can just say:</p>

	
	<%= render @users %>

	
<p>And it will do the same damn thing. IT'S WILD YO.</p>

<p>How this works is that when we call on the built in render method, behind the scenes we are calling on "to_partial_path." So when I say "render @users", I am also saying:</p>

	
 	@users.each do |user|
 		user.to_partial_path
 	end

 	
<p>The method to_partial_path finds the partial that matches the model name that defines the object. This works for all models that inherit from ActiveRecord::Base.</p>

<p>This even works for collections that belong to specific objects. While we could iterate through a collection, like a specific user's comments, and render that partial, like:</p>

	
	<% @user.comments.each do |comment| %>
  		<%= render comment %>
	<% end %>

 	

<p>We can instead just say:</p>


	

 	<%= render @user.comment %>

  	

<p>It gets even wilder! Because we can even render a collection of different objects from different collections. These are called collection partials:</p>


	

 	<%= render @user.favorites %> #--> renders favorite photos, comments, posts

 	<%= render [post1, comment2, comment3, post3, comment5] %>

  	
<p>Thank you for listening to me. But really it wasn't really hard to look this up. It was just partial work.</p>

<p>sources:</p>

<p><a href="https://robots.thoughtbot.com/rendering-collections-in-rails">Rendering Collections in Rails</a></p>
<p><a href="http://guides.rubyonrails.org/layouts_and_rendering.html">Rails Guides: Layouts and Rendering in Rails, Section 3.4.5: Rendering Collections</a></p>
