## World Borders Quiz

This game strengthens the player's geography through randomly generated multiple-choice questions.

For example -

* Which of these does not border Belize?

    * A. Mexico
    * B. Guatemala
    * C. Honduras

(The answer is Honduras.)

Try it [here](http://danielmoore.us/borders-quiz)!

You can create custom quizzes by playing with the URL. Examples -

* [Countries that end with "stan"](http://danielmoore.us/borders-quiz?custom=stan$)
* [Country quiz excluding bodies of water](http://danielmoore.us/borders-quiz?custom=^(?!.*(Sea|Gulf|Bay|Strait|Lake|Channel|Ocean|Rio|Bight)\b))
* [Country quiz with two answer choices](http://danielmoore.us/borders-quiz?num-choices=2)
* [Countries in Africa starting with map](http://danielmoore.us/borders-quiz?start=Guinea&depth=100&exclude-paths-through=Egypt;Morocco&start-map=Moundou+Chad&start-zoom=2&title=Africa)
* [U.S. states without starting map](http://danielmoore.us/borders-quiz?no-start-map&usa-states)
* [U.S. states that don't contain the letters 'a' or 'e'](http://danielmoore.us/borders-quiz?usa-states&custom=^(?!.*[ae])&title=USA+States+That+Don't+Contain+the+Letters+'a'+or+'e')
* [Canada and neighboring U.S. states starting with map](http://danielmoore.us/borders-quiz?usa-states&start-map=Canada_&start=Canada_)
* [Canada provinces, U.S. states, and Mexico states](http://danielmoore.us/borders-quiz?canada-provinces&usa-states&mexico-states)
* [Random quiz mode](http://danielmoore.us/borders-quiz?random)
* [Mega-quiz covering everything](http://danielmoore.us/borders-quiz?all)

(Google discontinued Fusion Tables on December 3, 2019. As a result, I've had to gut borders-quiz from 30 quiz modes to 6.)

### Development Guide

First install [Git](https://git-scm.com/) and [Node.js](https://nodejs.org/en/), then open your command prompt and run -

```
git clone https://github.com/denialromeo/borders-quiz
cd borders-quiz
npm install
npm start
```

Now you can play the game at [http://localhost:8000](http://localhost:8000)!

Adding a quiz is simple. Just add relevant entries to [borders.json](/build-question/borders.json) and [quiz-modes.json](/game/quiz-modes.json). You can also play with some settings in [game-settings.json](/game/game-settings.json) (e.g. more precise maps, prepending "the").

However, you must observe these rules or the game will break -

* The top-level labels of [borders.json](/build-question/borders.json) and [quiz-modes.json](/game/quiz-modes.json) *must* match.
* All entries in [borders.json](/build-question/borders.json) *must* be unique. Add trailing underscores to avoid conflicts with entries in existing quiz modes.
* If a territory is on an island and borders every other territory on that island (e.g. Haiti and the Dominican Republic), you *must* manually provide alternative answer choices in [question-settings.json](/build-question/question-settings.json).

(Running `npm run validate-data` will alert you to game-breaking data.)

### Known Bugs

* Territory names in more recent quiz modes aren't properly abbreviated on mobile.

* There's sometimes a distracting black flash when the maps load on Firefox. This has me stumped.

### Inspiration

The idea for this project was taken from this beautiful diagram in [*Algorithms*](https://www.amazon.com/Algorithms-Sanjoy-Dasgupta-ebook/dp/B006Z0QR3I/ref=sr_1_1_twi_kin_1?ie=UTF8&qid=1534812555&sr=8-1) by Dasgupta, Papadimitriou, and Vazirani.

![](inspiration.png)
