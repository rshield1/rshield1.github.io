---
layout: post
title:      "React | Redux | Rails -  This has been CHALLENGING!"
date:       2020-10-11 21:08:29 -0400
permalink:  react_redux_rails_-_this_has_been_challenging
---


Well for starters, duing the first week on project week, I wanted to build one certain project that I prepared a month in advance, breeze through that code by meeting the basic requirements for the project, and then refactor and add additional componentes during the second week  However, I had many days where I felt overwhelmed with long sleepless nights.  Between maintaining my career track prepping for mock interviews, working during the day, practicing coding challenges, and working on figuring out my project.  Maybe my ideas were too big at the time.  I'm not sure, but I had to dial back my ideas and focus on the task at hand.

- Project resources

During this entire project, It has been extremely challenging.  My first resource was obviously the learn lesson videos, my instructor, and labs dedicated to react/redux.  I  also used additional resorces, such as the React/Redux documentation, Dev Ed, on YouTube, Scrimba, and Udemy/Udacity courses.  I love to read the material, but I needed to see other material that would help me digest the logic of react and redux state mangement.


- Project idea # 1
Lynk - Social Media App - [](https://github.com/rshield1/lynk)

I was able to follow the format of Brad Traversy's video and use node/express/mongoDB on the back end.  This was the most intensive build, which took sleepless days and nights to complete.  From spinner components, to auth components, this pretty much covered everything in React, minus Hooks.  I needed to figure out authentication, which was pretty tough for me in rails, however the plan is to add authentication to my Gamer App in due time.

- Project idea # 2
Mantis - Pinterest App - [](https://github.com/rshield1/mantis-frontend)

This was made with love. I was able to learn more about hooks and context.  Although when I decided to wait until I completed the front-end to add redux, it became even tougher to rollback and add redux.  Also, I only had photos that I fetched, but I never added any additional photos.  I decided to hold off on adding redux, since I didn't have the time needed to dedicate to doing so.

- Project idea # 3 - [](https://github.com/rshield1/Gamer)
Gamer App - App to search and add games.  Now this is one that will cover all of the requirements needed  for the react/redux project.  I created and styled this app so people can view, and create games.  The user can persist a new game and also a new rating associated with the game.  You can also filter out the games, as I was able to implement a searchfield that uses the filter method to create a reactive searchfield. If you're not happy with the rating, you can delete it.  I will eventually incorporate more to make this application more user-friendly.

- Challenges

- React Hooks

Im still learning how to incorporate hooks more often, so I took a course on scrimba dedicated to react hooks.  I used information from the React course to add hooks into my Mantis application.  In my Context.js file I added hooks to reduce the complexity of state management.  

Hooks are functions that let you "hook" into React state and lifecycle features from functional components.  A certain built in know hook is useState.  It allows you to not need to convert your function into a class.

```
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);
```

- Redux reducers and actions

I struggled with reducers and actions throughout the cirriculum, however the more I continue to console.log, and debug through my errors, it gets easier to understand.  For example, with my Gamer App, I was frequently figuring out how to replace data with the previous data with the same id.  I have a case called delete rating that deletes the game's rating when you click the button.  I just needed to map over the games and match the ids to dispatch the task.  Heres the code in my reducer;
```
 case 'ADD_RATING':
              let games = state.games.map(game => {
                if (game.id === action.payload.id) {
                  return action.payload
                } else {
                  return game
                }
              })
```

Luckily I figured it out, and thought about the logic behind it by doing a little sudo code.

- Anonymous functions

I believe anonymouss functions are just one of those that are hit or miss at the moment.  Whenever I see code like this.. ()=>, I need to realize that not having the const "name of function" = () => Is throwing me off.  I tend to return to the javascript learn section to review and work on coding challenges in javascript.

- Did you know?

Did you know if you use const besides using function, you can avoid using .bind(this)?  Its like const knows that when you are inside the function, you arent referring to the function when you say "this", but the state of the class.  If you were to use the function using the function keyword, "this" is referring to the function itself.

- { connect } to store
knowing when to use { connect } from react-redux is still new, however I know that whenever I need information from the state, I'll need to use connect.  Its similar to using context, but without all of the complexities of redux.


I'm so ready to graduate!
