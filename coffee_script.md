# CoffeeScript

CoffeeScript is a language that renders Javascript using syntax similar to Ruby, effectively banishing the ugly. You know what I mean.

CoffeeScript is popular in Rails, and out of Rails because let's be honest Javascript is an ugly b.

## Translation

Because CoffeeScript is a whole new language and involves a whole lot of new syntax, it is rather tricky to pick up when starting out, as with all new languages. Luckily the CoffeeScript website provides us with a handy guide.

![CoffeScript.org](coffee-script-site.png)

### Basics

Essentially what CoffeeScript does is smooth out the Javascript logic. Gone are all the piles of curly braces and semicolons. Instead of using "this", we use an "@." When defining a function, instead of writing out "function" we use an arrow like so: "->". Additionally, CoffeeScript removes the necessity to explicitly return within any given function as CoffeeScript mimics the implicit return policy of Ruby.

For loops are also broken down into a simpler syntax. 

```
eat food for food in ['toast', 'cheese', 'wine']

===

var eat = function(food) {
  return `${food} eaten.`;
};

var ref = ['toast', 'cheese', 'wine'];
for (j = 0, len = ref.length; j < len; j++) {
  food = ref[j];
  eat(food);
}

```

Sources:

- http://coffeescript.org/
- http://railscasts.com/episodes/267-coffeescript-basics?autoplay=true
- 