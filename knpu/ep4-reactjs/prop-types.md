# Prop Types

Coming soon...

If you look at rep log list, it makes use of two prompts, highlighted row ID in on row click, 

but what 

guarantee is that rep log list is actually passed those components. I mean what guarantees that we didn't. For example, forget to pass in those props from rep logs the answer absolutely nothing in php, when you instantiate a class, when you instantiate an object, if that objects constructor has some required arguments, were forced to pass those arguments into that constructor, but with react components, there is nothing like that. There is simply no guarantee that we are past any of these prompts and that's especially a problem with Andro click because if you don't pass the unreal click here. Our whole application is going to break when someone clicks on a rope, so to fix that react to leverage is something called prompt types. In prototypes are actually installed, are actually live in an external library, so move over to your terminal and run yarn and prop dash types, dash dash depth. 

Beautiful. Now, the way that you add prop types to a specific component is you say rep, log list, dot prop types, equals, and then you pass an object where you describe all the different props that this component must have. To do that at the top, you need to import that new library in port prop types from prop types. And then at the bottom we can document our two props that we need. So we need highlighted row id and this can be prompt types that any. So we'll say this prop can actually be anything. And then on row click is the other one, and this isn't mean prep type stuff, funk. So this must be a function now for highlighted row id. I also could have used prop types dot number because it is a number right now, but later we're going to refactor our highly, our ids to be you, you ids, which are a string. 

So for now I'm just going to use prop types dot any. Now as soon as you do that, it's got a rep back to rep logs and instead of passing in a function, let's pass in a string. Cool, thanks this. When you move over and refresh, when you move over, you get an error and notice the page actually refreshed before I got here. That's thanks to the Dev server that we're running. Whenever we save a file, our browser automatically refreshes, which is kind of Nice. Anyway, as we see invalid prop on row click of type string supplied to rep log list. Expected function, that's what prep types give you. They give you early clear warnings when something went wrong. 

Now, as I mentioned earlier in Rep log list highlighted row ideas not really required. If we forget to pass the indoor component, it's fine. It just means that none of our rows are going to be highlighted, but if somebody forgets, but if we forget to pass in on row click, that's a problem because our code is actually going to fail down here when somebody clicks that row, so on row click is actually a required prop type to document that in forest that we're going to say.is required. Now back in read blogs, if we remove that entirely and move over. Yep. The prop on real quick is marked as required in rep log list, but it's valuable, 

undefined, awesome. 

So back in rep logs, let's Riyadh the on row click, but check it out when we type it, we're getting auto completion on that prop and that's because php storm notices that this is now defined, knows that this is now defined as a prop type and rep log list so it knows that it should auto complete that for us. That's really awesome. The other thing is that in rep log list before we had a prop types that were too big airs under each of these props here. That was basically php storm warning us that we had not done the prop. A prop types for these two props. Another spot that we have a props is actually in the top level rep log APP. We are relying on a with heart property passed to us and check this out. You can see the warning I was talking about earlier. It says with heart is missing and props validation. This is the heart is actually being passed for our top level entry file, so let's do the same thing. Let's add some prop types for that, so we'll import prop types 

from prop types. 

At the bottom we'll say rep log, APP dot prop types equals and we'll say with part is going to be a prop types got rule and it's not really required because if somebody doesn't pass it in then it will just look like false and we won't have any hearts. The one last place where we need to do prep types is actually in rep logs here. We actually depend on three different prompts, so maybe let's go copy the import statement from our rep log APP will import it. Then at the bottom we'll say rep logs. That profit types equals and notice this needs a with heart highlighted id and on row click, so I'm going to copy the with heart from rep log app, paste that here, and then we'd copy the other two props from rep log list and we'll paste those here. Now notice one thing I'm really missing a bit of a pattern that is really common. React in that is this pattern that lot of times you pass props into one component just so that component can pass them into another component. For example, in Rep log APP, we pass with heart highlighted roadie in real quick, but highlighted row and id and on real quick. They're never used in this component. We only need those so that we can pass them into rep log list. The child components. This on its own is just a really common thing in react and it's kind of annoying, but it's not necessarily a sign of a problem. 

There are ways to organize your code to alleviate this, but if you see this pattern coming up, don't panic. Nothing is necessarily wrong. Um, but you may be. Nothing is necessarily wrong. It's, it's a bit of an annoying thing, but it's fun. All right. The last thing that prop types is that their whole purpose is just to help us during development. They don't add any extra functionality to our code. And for that reason, sometimes when people do their production builder, their assets to save a little bit of space, they'll actually remove the prop types code in their production belt. Google for Babel Plugin, transform, react, remove prop types. This is a Babel plugin that can actually remove this stuff when Babel is doing its magic. So let's copy of the library name, move over and run yarn, add that library name, Dash, Dash Dev. While that's downloading, go back and out documentation. And the way that this 

works is in your babble, our file, you're supposed to add this configuration here that activates this plugin in production environment only except that we don't have a Babel RC file. We are using babble, but because we're using webpack encore, webpack is actually encore is actually handling our babble configuration internally. Fortunately it gives us a hook to modify that if we need to add some custom stuff. And you can do that by saying, configure babble and then passing that a function that takes in with one argument, we'll call it Babel config. So when encore builds all of the Babel configuration and then it's going to call our function and we can modify it if we want. So we need to add a end of key and then this configuration below it. So I'm a copy of the production plugins part and then we'll say banvel, config dot env equals an object and will paste the production plugins thing inside of there. It's safe to do this because if you, if you printed out the Babel config, it doesn't have a dot, doesn't have an end of key right now. So we're not overriding anything. We're adding a new key to Babylon thing 

just to make sure we didn't break anything. Go back to your terminal, find the server that runs encore, stopped that and then restart it. And it works without any problems. And right now we're still going to have the prop types inside of there if we refresh. But if we did a production and build those prop types would be gone.