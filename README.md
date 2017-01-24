# Koding a Quiz with Klossy

## Making Your Own Quiz

We decided to make a simple version of our Swarvoski Dating Symbol Quiz that you can edit and make your own. This guide has two parts, the first is a set of instructions for how you can make your own matching style quiz and the second is an explanation of how it works and a deeper dive into HTML, CSS, and Javascript, the languages of the web.

Matching quizzes are really fun and you've probably seen a bunch of them. They provide a person a series of questions that will determine some match, for example "Which Game of Thrones Character are You?" (other options - https://www.buzzfeed.com/sheridanwatson/which-supermodel-are-you?utm_term=.yuRZJY66B#.kp4lqnaaG - https://www.buzzfeed.com/robinedds/which-game-of-thrones-character-are-you - http://brainfall.com/quizzes/what-programming-language-are-you/#SyzpPbBPe - http://www.whowhatwear.com/which-fashion-designer-are-you-quiz ). Learning how they work is a great introduction to programming and lots of fun for a beginner project.

### Getting Started

The first step is to decide how you want to work on your quiz. The absolute easiest way is to get started with our [CodePen](http://codepen.io/kodewithklossy/pen/mRwOBZ?editors=1000). You should "Fork" ![Fork](https://dl.dropboxusercontent.com/s/q99k1o2uwsyuquh/2017-01-24%20at%2012.03%20PM.png) the CodePen to work on your own copy of it.

CodePen makes it super easy to get started because you can just start editing the HTML immediately and see your changes reflected below.

![Editing on CodePen](https://dl.dropboxusercontent.com/s/iwja72hk08cuvmz/2017-01-24%20at%2012.21%20PM.png)

You can minimize the CSS and JS because you'll only need to work with HTML.

If you're totally unfamiliar with how to edit HTML and have really never ever played with code, we highly recommend [CodeAcademy's HTML Course](https://www.codecademy.com/learn/learn-html-css) to get started.

You can also download a [zip of the project](https://github.com/kode-with-klossy/swarovski-dating-symbol-tutorial-2017/archive/master.zip) and open the [quiz.html](https://raw.githubusercontent.com/kode-with-klossy/swarovski-dating-symbol-tutorial-2017/master/quiz.html) (click "Save as..." to download) file on your own computer with your own [text editor](https://atom.io/) and browser. 

Once your setup so that you can edit the HTML and see changes, continue below!

### Creating the Quiz Content

The key to making your own quiz is picking a few possible matches for the person. For example, our Dating Symbol Quiz matches you with 1 of 5 possible Swarvoski Charms. You are either a "Heart", "Moon", "Evil Eye", "Lock and Key", or "Star" charm. Each time you pick an answer in the quiz, our code is adding a point to one charm's score. At the end of the quiz, the charm with the most points is how we match you.

If you are making your own quiz, it's a good idea to pick 3-5 things you are going to match people to. Your quiz might be "What Pie are You?" (in honor of my favorite upcoming holiday, Pi Day on March 14th) and the answers match a person to either a "Blueberry Pie", a "Rasberry Pie", "A Ruhbarb Pie", "Pumpkin Pie", or "Apple Pie".

Once you've figured out what your quiz is about and what matches you'll provide, the next step is to write your questions and answers, corresponding each answer to a match. For example, the first question in our Dating Symbol Quiz is:

```
1. What do you do with your restaurant leftovers?

A. Eat them the next day for breakfast.
B. Forget about them till my fridge smells like a dead hand.
C. Spill them on myself as soon as I get in the car because of course.
D. There’s no such thing as leftovers I eat it all I’m a champ.

If you pick answer A, the "Evil Eye" charm will get a point.
If you pick answer B, the "Lock and Key" charm will get a point.
If you pick answer C, the "Heart" charm will get a point.
If you pick answer D, the "Star" charm will get a point.
```

You get to make up these pairings, have fun with it, be creative. For example, in our Pi Day Quiz, we might have a question with the following answers:

```
1. What's your favorite holiday?

A. Halloween
B. Memorial Day
C. 4th of July
D. Labor Day

If you pick answer A, the "Pumpkin Pie" will get a point.
If you pick answer B, the "Ruhbarb Pie" will get a point.
If you pick answer C, the "Apple Pie" will get a point.
If you pick answer D, the "Blueberry Pie" will get a point.
```

It's a good idea to plan out your quiz with all the matches, questions, answers, and scoring before you start editing your code. Ours looked something like:

```
2. Your phone dies, what do you do?

A. Go back to sleep and hope it was a terrible dream. (Lock and Key)
B. Have a technology-free adventure. (Moon)
C. Start a new life wherever I am, without GPS I’ll never find home again. (Heart)
D. Ask for a stranger’s phone then realize I don’t know any numbers by heart. (Evil Eye)
```

Okay, once you have all your quiz content planned out, you can start editing the code.

### Editing the Code

#### Adding Winning Matches

The first thing to edit is the winning match section of the code, all the way at the bottom of the HTML. Scroll to the bottom of the HTML and you'll find a series of `<div>`s that look like:

```html
<div id="heart" class="winner">
  <h1>You are a Heart</h1>
  
  <img src="/images/2017-dating-symbol-quiz/vd-quiz-heart-white.gif">

  <p>
    You wear your emotions on your sleeve and follow your heart.
  </p>

  <a href="#" class="retake">Retake Quiz</a>
</div>
```

Each of these `<div>`s represents a potential match for the quiz. Even though the code has five of these winner `<div>`s, none of them are immediately visible on the page when the quiz is loaded and only one winner `<div>` will even be displayed when the quiz is submitted.

Your next job is to have one winner `<div>` for each of your potential matches. The match has a title, which we put in the `<h1>` tag.

Our matches then have an image in the `<img>` tag, but you can take those out or provide your own image URL by changing the value of the "src" attribute. <a href="https://support.google.com/websearch/answer/118238?hl=en">You can search google images for image URLs.</a>

Finally there is a `<p>` tag which includes a description of the winning match.

The most important thing you need to do to each winning `<div>` is change the value of the `id` attribute of the `<div>`. 

```
<div id="heart" class="winner">
```

You need to change the `id` to to a word for your match. For example, the winner `<div>` for the Moon symbol will open with `<div id="moon" class="winner">` and the winner `<div>` for the Lock and Key will open with `<div id="lock-key" class="winner">`. We are using `moon` and `lock-key` as our match words. The words your code uses for the `ID` of the winner `<div>` is important and will correspond to the answers to our questions we're going to code shortly. 

All the winner `<div>`s for our Dating Symbol quiz looks like:

```html
<div class="quiz-results">
  <div id="heart" class="winner">
    <h1>You are a Heart</h1>
    <img src="http://kodewithklossy.com/images/2017-dating-symbol-quiz/vd-quiz-heart-white.gif">
    <p>
      You wear your emotions on your sleeve and follow your heart.
    </p>
    <a href="#" class="retake">Retake Quiz</a>
  </div>

  <div id="lock-key" class="winner">
    <h1>You are a Lock and Key</h1>
    <img src="http://kodewithklossy.com/images/2017-dating-symbol-quiz/vd-quiz-key-white.gif">
    <p>
      You’re genuine and slightly mysterious.
    </p>
    <a href="#" class="retake">Retake Quiz</a>
  </div>

  <div id="evil-eye" class="winner">
    <h1>You are an Evil Eye</h1>
    <img src="http://kodewithklossy.com/images/2017-dating-symbol-quiz/vd-quiz-eye-white.gif">
    <p>
      Your positivity is what guides you.
    </p>
    <a href="#" class="retake">Retake Quiz</a>
  </div>


  <div id="star" class="winner">
    <h1>You are a Star</h1>
    <img src="http://kodewithklossy.com/images/2017-dating-symbol-quiz/vd-quiz-star-white.gif">      
    <p>
      You’re down to earth and loyal.
    </p>      
    <a href="#" class="retake">Retake Quiz</a>
  </div>


  <div id="moon" class="winner">
    <h1>You are a Moon</h1>
    <img src="http://kodewithklossy.com/images/2017-dating-symbol-quiz/vd-quiz-moon-white.gif">            
    <p>
      You’re extremely creative and contemplative.
    </p>
    <a href="#" class="retake">Retake Quiz</a>
  </div>
</div>
```

This HTML defines our winner's as `heart`, `lock-key`, `evil-eye`, `star`, and `moon`. These words, which all appear at the end of each winner `<div>`'s id (as in `heart` or `evil-eye`), are going to be used when we code the answers to questions of the quiz. You get to choose them for your winning matches, all you need to do is be consistent with their naming and usage.

Remember, as you edit your winner `<div>`s and reload the quiz in your browser, you won't see the `<div>`s because they are hidden. Don't worry about this, we'll be debugging and fixing anything that's broken once we're a little further along.

#### Adding Questions and Answers

Now that we've got all our content defined and have coded our matching winner `<div>`s, it's time to code the questions and answers for our quiz. Just like all the winner `<div>`s' HTML had a consistent structure, all the questions and answers will follow a common template shown below:

```html
<h2>1. What do you do with your restaurant leftovers?</h2>
<ul>
  <li data-answer="evil-eye">Eat them the next day for breakfast.</li>
  <li data-answer="lock-key">Forget about them till my fridge smells like a dead hand.</li>
  <li data-answer="heart">Spill them on myself as soon as I get in the car because of course.</li>
  <li data-answer="star">There’s no such thing as leftovers I eat it all I’m a champ.</li>
</ul>
```

Each question and answer set begins with an `<h2>` tag that is the main text of the question. Underneath the question's `<h2>` is a set of answers grouped together within a `<ul>` (Unordered List) tag. All the answers for this question are represented by individual `<li>` (List Item Tag) nested inside the `<ul>`'s opening and `</ul>` closing tag. The question above has 4 potential answers because it has 4 `<li>`.

The most important part of the question and answers' code is the `data-answer` attribute within the `<li>`. The value of the `data-answer` attribute of the `<li>` corresponds to the scoring for the quiz match. If you select the first answer above, where the `data-answer` attribute is set to `evil-eye`, you are gaining a point toward your match with the Evil Eye symbol. Additionally, you'll notice that `evil-eye` corresponds to the word we used in the winner `<div>` for the Evil Eye symbol, `<div id="evil-eye" class="winner">`. As long as the `data-answer` value matches a winner `<div>` everything will work. In programming, this sort of consistent matching of a pattern is called a convention.

You can add as many questions as you'd like and you can have as many answers per question. Not every potential winner needs to be represented by an answer in every question, you can mix and match.

As you're adding questions and answers, play with the quiz, you should be able to see it working as expected. If you select an answer and submit the quiz (you don't have to answer all the questions to submit the quiz), you should see the winner `<div>` that corresponds to the answer's `data-answer` attribute appear. If it doesn't, make sure everything is spelled correctly. Debugging is a natural part of the process, just go slow, pay attention. You can always start with [a fresh copy](http://codepen.io/kodewithklossy/pen/mRwOBZ?editors=1000#0).

### Recap - `tl;dr` (Too Long; Didn't Read)

The steps to editing the quiz are:

1. Prepare the quiz's questions and answers first. Make sure you decide on what you're matching and what the winners are in advance. Correlate each answer to one of the potential matches so that you know how the quiz will be scored.

2. Code the winning match `<div>`s first. Remember, they won't be visible on the page but you'll be able to test and fix everything soon. Pay attention to the `id` attribute of the winner `<div>`s as you will have to re-use those as the answer key in the next step.

3. Add as many questions and answers as you want. Each answer must have a `data-answer` attribute whose value corresponds to one of the `id`s of the winning divs you created above.

4. Play with your quiz! Debug, clean things up and make sure everything is working! You're done!

## How the Quiz Actually Works

Pt 2 coming soon...




