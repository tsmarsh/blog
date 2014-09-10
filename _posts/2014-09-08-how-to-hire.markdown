---
layout: post
title: "How to Hire"
date: 2014-09-08 19:24
comments: true
categories: 
---

We have a quality problem in technology. We talk about bugs, we talk about size and complexity but we rarely talk about hiring. The fact today is that there are more jobs for developers than developers. The market knows this. Which is why tech jobs pay so well, but it has also meant that the industry is saturated with people motivated by solely by the money. This would be less of a problem if it didn’t seem to be always at the price of quality.

One of the cute things about software is that you can’t see it. In my last post I equated Rails development to assembling Ikea furniture. The biggest fault in that analogy is that you can see what you are buying with Ikea. Even if you haven’t taken a single wood working class, you can get a sense for how well made the furniture is. Worse, it is really easy to fake quality in software: “Works on my machine” is the battle cry of crappy developers everywhere. It is really easy to make software work for one user with fake data for the 30 minutes it takes to demo or sell a software. Too easy. 

Perhaps the most damning thing about the software industry is that it is filled with people who can’t code. Not even a little bit, and yet they have years of experience and decent college degree. They might be able to sound technical, they might even be able to do math and logic problems on white boards. But they can’t code for shit.

Why do I feel like I can make that statement?

Eight years of hiring developers and ten years of being hired as a developer. I think I can count the weeks where my current employer weren’t looking to hire a developer on one hand. There is a lot of churn in the software industry. Mostly because finding a good dev is hard, expensive and in order to secure one, starting salaries are often 15-20% above your current salary, so people leave and take a 15% raise, rather than the 3% your felt was reasonable given thats what the company grew by last year.


## How do you get good developers?

The following steps are the minimum you should be doing if you want to make sure the people you hire to develop your product can actually code and be useful team members with the minimum of impact to your development team.


### A Resumé / CV Screen ### 

**Dev Cost**: 0 minutes
**Effectiveness**: 500 &#8594; 100 candidates

A non-technical HR person should run through the credentials and make sure that I will fit the culture and the business needs of the company. As a candidate I used to hate this step, as a technical interviewer I value its ability to reduce the number of interviews and code reviews I have to do.

This step hinges on you HR departments ability to gauge a personality in a 15 minute conversation that is, in theory, just running down your resumé. It should remove anyone who has poor communication skills, has a dodgy work history or just doesn’t sound that interested. They should also outline the process. If a candidate is not interested in a code review and pairing interview this is an excellent opportunity to avoid wasting any more of each others time.

Most companies employee this strategy. Its an easy win.


### A Coding Exercise ### 

**Dev Cost**: 30 minutes per reviewer per applicant
**Effectiveness**: 100 &#8594; 25 candidates

It is reasonable of a future employer, given the dearth of talent in the industry, to make sure that I can complete a 1-2 hour assignment that demonstrates that I can actually code and think logically. The exercise should be simple: [kata](http://codekata.com/) or something similar. However, most companies create their own twist on a classic and use that.

The aim isn’t get a candidate to solve current business problem. It is to remove the 75% of candidates that have a valid work experience but still don’t know how to code to a professional level. 

This may rule out some good candidates. To reduce those people I would offer advice similar to this:

* Make sure your code runs
* Use the most idiomatic build system
	* Java &#8594; [Maven](http://maven.apache.org/) 
  	* Ruby &#8594; [bundler](http://bundler.io/) / [rake](https://github.com/ruby/rake)
  	* Python &#8594; [virtualenv](http://virtualenv.readthedocs.org/en/latest/) 
  	* Clojure &#8594; [leiningen](http://leiningen.org/)
* Make sure your tests pass
* Use a DVCS ([git](http://git-scm.com/) or [mercurial](http://mercurial.selenic.com/))
* Do the simplest thing that works

It is amazing how few people, even when asked, still don’t include unit tests, almost as amazing as the number of submissions that need a little bit of help to get running. You need to gauge for your own purposes where you continue to assess submissions that don’t even pass these steps, bounce them back to the candidate (human error is a thing), or reject on principle. 

### A Technical Phone Interview### 

**Dev Cost**: 30 &#8594; 60 minutes
**Effectiveness:** 25 &#8594; 3 candidates

Communication about technical subjects is the differentiator between an average developer and a good developer. Whilst there is value in developers with poor communication skills, but good coding skills, that value is significantly below the market rate. There is no value in a developer with good verbal skills, but no coding ability. Because you have already done the code exercise, you are somewhat confident that you, at worse have the former.

The interview should cover new technologies, the direction the industry, the effectiveness of practices and the _trading_ of battle stories. 

Most candidates are working and most interviews are during office hours. So candidates are probably walking around, in their car, or hiding in a cupboard, not sat in front of a computer or whiteboard. You have already seen that they can code via the exercise.

The purpose of this exam is just to get a sense of where the candidate is at. Are they a lead developer, a junior developer. It covers experience and breadth of knowledge. It should re-enforce what you have already learned from the pairing exam. 

This is also an excellent time to ask questions about the design of their code submission, that would otherwise cause you to reject the candidate. 

### Face-to-Face Pairing Exercise ### 

**Dev Cost**: 60 &#8594; 120 minutes
**Effectiveness:** 3 &#8594; 1 candidates

Pairing is a great practice that really shines in interview situations. The ability of another developer to work closely with other developers cannot be understated. 

This is the most expensive phase of the interview process but it is definitive. At the end of a pairing exam a candidate will have designed, created and modified code, the definition of their future role. With any luck, whilst they were doing it, they were talking to your developers about why they were doing. If they were really good, your developer will walk away feeling like they learned something. If they can’t do it, it cost you an hour of one developers time and whatever it cost to get them into the office. Significantly cheaper than hiring and hoping. 


## Conclusion

The four steps above represent the absolute minimum that I expect to go through when I’m looking to change jobs. They are not difficult to put in place, and they are proven to work. They should reduce the amount of time your dev team spends interviewing, and dramatically increase the standards on your dev team. It also empowers your dev team to form around their own values, with three of four steps being completely controlled by them.

I didn’t mention references. If they can code, and you have proven that they can code, and you have spend time talking to me, what do you expect to learn from talking to an ex-employer that you don’t know, that the candidate themselves suggested.

I didn’t mention education. In my experience education is no indicator of developer performance. I tend to have a preference for computer science graduates, but some of the best devs I’ve worked with had nothing beyond a high school diploma.  Trust the process. If they can get through these steps, they are good enough.

I also think that it is important to reiterate that none of these steps represent an unreasonable hurdle. This is a very low bar. It terrifies me how few developers with >5 years of experience and degree fail the coding exercise, never mind a pairing exam. 

The only way we can improve our industry is by making it impossible for bad coders to get jobs.  


### Extra Credit ###
Practices I have seen and liked, but are added extras, not a minimum:

* **The [Wonderlic](http://www.wonderlic.com/) Test:** I'm not sure how I feel about making IQ a minimum requirement for hiring, but the company where I worked that required this was an awesome working environment. It is elitist, it does affect culture, but that might be what you are looking for. 

* **Uncomfortable Pairing:** Forcing you to pair with someone who doesn't know the language you are pairing in. Forcing someone to pair in a language they are not familiar with. If you are hiring someone you expect to have good leadership skills or has said that they "learn quickly" at any point in the process make them prove it. It takes about an hour and you really get to see how a candidate thinks and reacts in a high pressure environment. Remember, good developers find developing to be fun. What is more fun than playing with a new language?!?

* **Presentation:** Ask a candidate to give a presentation on a chapter from a book that is fundamental to your culture. Indicates how serious a candidate is about the job. Helps you better gauge their abilities to communicate







