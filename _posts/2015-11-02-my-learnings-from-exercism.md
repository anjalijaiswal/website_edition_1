<!-- learnings.md -->
---
layout: post
title: "Anjali Jaiswal's Blog"
date: 2015-11-02
---

One day i stumbled upon this awesome site called ["Exercism.io"](http://exercism.io/). It mainly focuses on improving your skills via Deep Practice & Crowdsourced Mentorship, Strengthening your problem-solving skills by guiding others through the process. I got hooked onto it and  then i thought why not share my learnings with you all. One alert though, i am a ruby programmer so they are mostly ruby based.

Things To Keep In Mind

Before tackling any program/problem/challenge you should keep certain points in your mind. Some are general, some are language specific & here they are:

Some questions you might want to ask yourself:(credit: remcopeereboom)

  1.  Am I adhering to the Single Responsibility Principle?
  2.  Is all my code on the same abstraction level?
  3.  Can I combine conditional clauses?
  4.  How does my API look to clients of this code (i.e. how do other classes interact with this class)?
  5.  Do I have duplication?
  6.  What requirements are likely to change? Would I be able to implement such changes painlessly? [Note that I am not saying that you should normally guess what future requirements are, but it can be helpful on exercism]
  7.  Use Private, that way you limit the public API of any class. It's considered a good practice to expose as few methods as possible, so you don't come up with a "fat interface" and has to maintain a lot of methods that probably nobody else uses (this is troublesome when you want to refactor your code but you aren't sure if somebody is using method x or not).

If you are using in-built methods you should understand them first, like how they are working, what are the pros &cons. In which use case you should use them. Don’t assume dig them up. Some examples:

Difference between p & puts:
p foo does puts foo.inspect, i.e. it prints the value of inspect instead of to_s, which is more suitable for debugging (because you can e.g. tell the difference between 1, "1" and "2\b1", which you can't when printing without inspect).

to_a is super-expensive on big ranges.

Use string interpolation only when necessary.

These were general things, next section is more ruby specific. I have described what i learned from individual problem. My code is uploaded on ["github"](https://github.com/anjalijaiswal/exercism). You can take a look there. Also i have explained why i used certain in-built ruby methods. I have highlighted some specific things that you should consider in general.

<!-- accumulate -->
1. 2 ways to yeild a block in ruby 
    a) yield 
    b) call
      def speak(&block)
         puts block.call
       end 
    read [“ZOMG WHY IS THIS CODE SO SLOW?”](http://confreaks.tv/videos/rubyconf2010-zomg-why-is-this-code-so-slow) 
2. a(&:upcase) : you are passing a reference to the block (instead of a local variable) to a method. Also Symbol class implements the to_proc method which will unwrap the short version into it's longer variant.

3. yield returns the last evaluated expression (from inside the block). So in other words, the value that yield returns is the value the block returns.

4. If you want to return an array use map/select depending on situation. You dont need to intialize an array & return it.

<!-- anagram -->
1. anagrams are same if sorted.
2. select will return element if condition satisfies. So in case of conditions use select over map/each.

<!-- beer-songs -->
[follow](http://red-badger.com/blog/2014/08/20/i-spent-3-days-with-sandi-metz-heres-what-i-learned/)

<!-- binary -->
1. Used map.with_index so no need to initialize another variable & directly applying inject on the result.

<!-- bob -->
1. Start simple. Try to make test pass in a very easy way.

<!-- etl -->
Use of each_with_object: (but for ths, i will keep my soltn ; to much complex)
  
  input.each_with_object({}) do |(score, letters), result|
    letters.each do |letter|
      result[letter.downcase] = score
    end
  end

<!-- food-chain -->
Same theme as beer-song 

<!-- grade-school -->
1. Initialize an empty hash & and declare value as array.
2. To sort a hash & return a hash @grades.sort.to_h.

<!-- grains -->
Sometimes solution could be a single word. You don't need to iterate(over 64 values). In this example total is a series of 
(2n-1) where n is 2**(n-1).

<!-- hamming -->
1. Raise could be another method. Alwayz look out for single responsibility principle.
2. Select & count are perfect methods here.

(credit: alanwillms)
It's considered a good practice to expose as few methods as possible, so you don't come up with a "fat interface" and has to maintain a lot of methods that probably nobody else uses (this is troublesome when you want to refactor your code but you aren't sure if somebody is using method x or not).

In this exercise, the only method being called is self.compute, so this means you could make self.raise_size_mismatch private and avoid exposing it.

<!-- hello-world -->
1. You can pass default argument to a ruby method :
  def hello(name = 'world')
    #some data
  end

<!-- leap -->
You can minimize loop:
    if year % 4 == 0 && year % 100 == 0 
      year % 400 == 0 ? true : false
    elsif year % 4 == 0
      true
    else
      false
    end
to:
    year % 400 == 0 || year % 4 == 0 && year % 100 != 0

<!-- phone-number -->
1. Intresting use of sub:
    '0987654321'.sub(/(\d{3})(\d{3})/, "(\\1) \\2-") => "(098) 765-4321"
2. Can return a part of string:
    '0987654321'[0..2] => '098'

<!-- raindrops -->
1. Assing common values as constant.
2. Avoid unnecessary computing. For example you only need to check if 3,5 & 7 are factors.
    
<!-- robot-name -->
1. shuffle method # Array (Can be applied to a-z but will be futile for 0-999 as it takes lots 
    of memory & computation)
2. Default assignment ||=

<!-- series -->
map(&:to_i)

That’s it for now. Stay tuned for more of my technical musings. You can also mention in comments how this blog helped you or if i missed something that should be included. Sayonara for now!

