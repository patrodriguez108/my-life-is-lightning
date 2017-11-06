Javascript:

function getRandomColor() {
  var letters = '0123456789ABCDEF';
  var color = '#';
  for (var i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * 16)];
  }
  return color;
}

$(document).ready(function() {
 	$(".coffer").click(function() {
 		$("body").css("background-color", getRandomColor());
 	});
 });


CoffeeScript:

getRandomColor ->
  letters = '0123456789ABCDEF'
  color = '#'
  for i in [0..6]
    color += letters[Math.floor(Math.random() * 16)]
  color

$(document).ready ->
  $('.coffer').click ->
    $('body').css 'background-color', getRandomColor()
    return
  return