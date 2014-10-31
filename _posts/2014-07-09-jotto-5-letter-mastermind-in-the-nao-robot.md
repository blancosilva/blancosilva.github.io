---
layout: post
title: "Jotto (5-letter Mastermind) in the NAO robot"
comments: true
---

<p style="text-align:center;">
    <iframe width="595" height="365" src="//www.youtube.com/embed/xQVjHmyD770" frameborder="0" allowfullscreen></iframe>
</p>

<!-- <p><iframe width="420" height="315" src="http://youtu.be/xQVjHmyD770" frameborder="0" allowfullscreen></iframe></p> -->

I would like to show how to code the NAO robot to beat us at *Jotto* (5-letter Mastermind) with `python` in `Choregraphe`. I will employ a brute force technique that does not require any knowledge of the English language, the frequency of its letters, or smart combinations of vowels and consonants to try to minimize the number of attempts. It goes like this:

1. Gather all 5-letter words with no repeated letters in a list.
2. Choose a random word from that list---your guess---, and ask it to be scored ala Mastermind.
3. Filter through the list all words that share the same score with your guess; discard the rest.
4. Go back to step 2 and repeat until the target word is found.

Coding this strategy in `python` requires only four variables:


* `whole_dict`: the list with all the words
* `step = [x for x in whole_dict]`: A copy of `whole_dict`, which is going to be shortened on each step (hence the name). Note that stating `step = whole_dict` will change the contents of `whole_dict` when we change the contents of `step` --- not a good idea.
* `guess = random.choice(step)`: A random choice from the list `step`.
* `score`: A string containing the two digits we obtain after scoring the guess. The first digit indicates the number of correct letters in the same position as the target word; the second digit indicates the number of correct letters in the wrong position.
* `attempts`: optional. The number of attempts at guessing words. For quality control purposes.


At this point, I urge the reader to stop reading the post and try to implement this strategy as a simple script. When done, come back to see how it can be coded in the NAO robot.


First, a screenshot of the `root` view in choregraph. Note the simplicity of the code.

<p style="text-align:center;"><img src="https://farm4.staticflickr.com/3910/14425999857_b6500621b4_d.jpg" alt="mastermind.png" style="width:75% border:2px solid black;"></p>

The first box, `ALMemory starter`, is a *script box* where we define all variables needed to run the program --- old school. This is the code of that box:

{% highlight python %}
from urllib2 import urlopen

def no_repeats(word):
        " Boolean: indicates whether a word has repeated letters "
    new_word = "
    for letter in word:
        if letter not in new_word:
            new_word += letter
    return new_word == word

# Get a list of 5-letter words from the following URL
file = urlopen("http://www.math.sc.edu/~blanco/words.txt")
words = file.read().split("\n")
file.close()

# remove words with repeated letters
words = filter(lambda x: len(x)>0, words)
words = filter(no_repeats, words)

class MyClass(GeneratedClass):
    def __init__(self):
        GeneratedClass.__init__(self)
        pass

    def onLoad(self):
        # We start by creating a proxy to the memory of the robot,
        # where we will insert all the needed variables
        self.memoryProxy = ALProxy("ALMemory")
        pass

    def onUnload(self):
        pass

    def onInput_onStart(self):
        # These are the variables we need:
        self.memoryProxy.insertData("whole_dict", words)
        self.memoryProxy.insertData("step", [x for x in words])
        self.memoryProxy.insertData("attempts", 0)
        self.memoryProxy.insertData("score", "00")
        self.memoryProxy.insertData("guess", None)
        self.onStopped()
        pass

    def onInput_onStop(self):
        self.onUnload()
        pass
{% endhighlight %}

The second box, `Deal with my word`, is a *flow diagram* containing two boxes:


* One simple *script box*, `Say the word`. This box performs the random choice from `step`, stores it in the variable `guess`, and increments the value of `attempts` by one. It asks then the player if `guess` is the correct word --- and spells it, just in case.
* A *speech recognition box* that expects a yes/no answer.

<p style="text-align:center;"><img src="https://farm4.staticflickr.com/3898/14610327804_466959a9a5_d.jpg" alt="deal.png" style="width:75% border:2px solid black;"></p>

This is the code of `Say the word`:

{% highlight python %}
from time import sleep
from random import choice

class MyClass(GeneratedClass):
    def __init__(self):
        GeneratedClass.__init__(self)
        pass

    def onLoad(self):
        self.talkProxy = ALProxy("ALTextToSpeech")
        self.memoryProxy = ALProxy("ALMemory")
        pass

    def onUnload(self):
        pass

    def onInput_onStart(self):
        step = self.memoryProxy.getData("step")
        guess = choice(step)
        self.memoryProxy.insertData("guess", guess)
        attempts = self.memoryProxy.getData("attempts")
        self.memoryProxy.insertData("attempts", attempts + 1)
        self.talkProxy.say("Is it %s?" % guess)
        sleep(1)
        for letter in guess:
            self.talkProxy.say(letter)
            sleep(1)
        self.onStopped()
        pass

    def onInput_onStop(self):
        self.onUnload()
        pass
{% endhighlight %}

A *switch case* is next: if the player says "yes", the program concludes with the *script box* `Success!`, that states the number of attempts. The code is simple, and it illustrates once again the way to access data from `ALMemory`. The only relevant portions of the code on that box are the methods `onLoad` and `onInput_osStart`:

{% highlight python %}
    def onLoad(self):
        self.talkProxy = ALProxy("ALTextToSpeech")
        self.memoryProxy = ALProxy("ALMemory")
        pass

    def onInput_onStart(self):
        attempts = self.memoryProxy.getData("attempts")
        self.talkProxy.say("Wonderful!  I got it in %s attempts!" % str(attempts))
        pass
{% endhighlight %}

If the player says "no", we retrieve the two scores with two *flow diagram* boxes: `First Score` and `Second Score`. I will present the structure and code of the latter, and leave the code of the former as an exercise.

<p style="text-align:center;"><img src="https://farm4.staticflickr.com/3900/14425751180_279c59f295_d.jpg" alt="secondscore.png" style="width:75% border:2px solid black;"></p>

The first box is a simple *Say* that asks for the score. The second box is a *Speech Recognition* box that expects any digit from 0 to 5. The third is a *script box* that receives the second box output (as a `string`), and performs the following operation (only `onLoad` and `onInput_onStart` are shown):

{% highlight python %}
    def onLoad(self):
        self.memoryProxy = ALProxy("ALMemory")
        pass

    def onInput_onStart(self, p):
        score = self.memoryProxy.getData("score")
        score = score[0] + p
        self.memoryProxy.insertData("score", score)
        self.onStopped()
        pass
{% endhighlight %}

And finally, the *script box* `Say the score`. This is where the magic happens. In this box we receive the complete score, and filter all the words from `step` to eliminate those that do not share the same score as `guess`. We perform that with the following code:

{% highlight python %}
def compute_score(guess, target):
        " This function scores guess against target,
            mastermind style "
    correct = 0
    moved = 0
    for x in range(5):
        if guess[x] in target:
            if guess[x] == target[x]:
                correct += 1
            else:
                moved += 1
    return str(correct)+str(moved)

def register_score(score, step, guess):
        " a simple fliter to eliminate unwanted words from step "
    return filter(lambda x: compute_score(guess, x)==score, step)

class MyClass(GeneratedClass):
    def __init__(self):
        GeneratedClass.__init__(self)
        pass

    def onLoad(self):
        self.memoryProxy = ALProxy("ALMemory")
        self.talkProxy = ALProxy("ALTextToSpeech")
        pass

    def onUnload(self):
        pass

    def onInput_onStart(self):
        score = self.memoryProxy.getData("score")
        step = self.memoryProxy.getData("step")
        guess = self.memoryProxy.getData("guess")
        self.talkProxy.say("So, the score of %s is %s %s" % (guess, score[0], score[1]))
        step = register_score(score, step, guess)
        #self.talkProxy.say("We are down to %s words" % str(len(step)))
        self.memoryProxy.insertData("step", step)
        self.onStopped()
        pass

    def onInput_onStop(self):
        self.onUnload()
        pass
{% endhighlight %}

That is all! I hope you enjoy playing *Jotto* with your NAO. The code can be greatly improved by adding motions in the different steps, or implementing better winning strategies. With brute force, NAO is able to find your word in about 5 attempts (as average, of course). Do you think you can find a strategy that brings this number down to 4 attempts? If so, I would love to hear about it.

