# Readings: REST
## Read:07 - APIs continued

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-07).

### For this class, I will be reading from these resource: `What Google Learned From Its Quest to Build the Perfect Team` and `How I explained REST to my brother` .

### :pushpin: [What Google Learned From Its Quest to Build the Perfect Team](https://www.nytimes.com/2016/02/28/magazine/what-google-learned-from-its-quest-to-build-the-perfect-team.html)
### :pushpin: [How I explained REST to my brother](https://gist.github.com/brookr/5977550)


## Article 1: What Google Learned From Its Quest to Build the Perfect Team

The technology industry is not just one of the fastest growing parts; it is also increasingly the world’s dominant commercial culture. And at the core of Silicon Valley are certain self-mythologies and dictums: Everything is different now, data reigns supreme, today’s winners deserve to triumph because they are cleareyed enough to discard yesterday’s conventional wisdoms and search out the disruptive and the new.

The paradox, of course, is that Google’s intense data collection and number crunching have led it to the same conclusions that good managers have always known. In the best teams, members listen to one another and show sensitivity to feelings and needs.

The fact that these insights aren’t wholly original doesn’t mean Google’s contributions aren’t valuable. In fact, in some ways, the ‘‘employee performance optimization’’ movement has given us a method for talking about our insecurities, fears and aspirations in more constructive ways. It also has given us the tools to quickly teach lessons that once took managers decades to absorb. Google, in other words, in its race to build the perfect team, has perhaps unintentionally demonstrated the usefulness of imperfection and done what Silicon Valley does best: figure out how to create psychological safety faster, better and in more productive ways.

Project Aristotle is a reminder that when companies try to optimize everything, it’s sometimes easy to forget that success is often built on experiences — like emotional interactions and complicated conversations and discussions of who we want to be and how our teammates make us feel — that can’t really be optimized. Rozovsky herself was reminded of this midway through her work with the Project Aristotle team. ‘‘We were in a meeting where I made a mistake,’’ Rozovsky told me. She sent out a note afterward explaining how she was going to remedy the problem. ‘‘I got an email back from a team member that said, ‘Ouch,’ ’’ she recalled. ‘‘It was like a punch to the gut. I was already upset about making this mistake, and this note totally played on my insecurities.’’


## Articel 2: How I explained REST to my brother

1. **Roy Fielding**
He helped write the first web servers, that sent documents across the Internet… and then he did a ton of research explaining why the web works the way it does. His name is on the specification for the protocol that is used to get pages from servers to your browser.

2. **How web works**
HTTP tells the browser what protocol to use. It is capable of describing the location of something anywhere in the world from anywhere in the world. It's the foundation of the web. The whole world wide web is built on an architectural style called **REST**. **REST** provides a definition of a `resource`.
A web page is a “representation” of a resource. A resource has only a single representation. 

3. **URL**
Those URLs tell the browser that there's a concept somewhere. A browser can then go ask for a specific representation of the concept. Specifically, the browser asks for the web page representation of the concept.
URL is so important because it let's all of these systems tell each other about each other's nouns.

4. **“Web Services” - "APIs"**
The basic concept is that machines could use the web just like people do.
Computers can use those same protocols to send messages back and forth to each other. 
But none of the techniques we use today work well when you need to be able to talk to all of the machines in the entire world. Because they weren't designed to be used like that. When Fielding and his buddies started building the web, being able to talk to any machine anywhere in the world was a primary concern. Most of the techniques we use at work to get computers to talk to each other didn't have those requirements. You just needed to talk to a small group of machines.

5. **Redirect**
A way of having one machine tell another machine about a resource that might be on yet another machine.

6. **Nouns and verbs**
HTTP—this protocol Fielding and his friends created—is all about applying verbs to nouns. For instance, when you go to a web page, the browser does an HTTP GET on the URL you type in and back comes a web page.
Web pages usually have images. Those are separate resources. The web page just specifies the URLs to the images and the browser goes and does more GETs using the HTTP protocol on them until all the resources are obtained and the web page is displayed. But the important thing here is that very different kinds of nouns can be treated the same. Whether the noun is an image, text, video, an mp3, a slideshow, whatever. I can GET all of those things the same way given a URL.

7. **GET**
It is an important verb especially when you're using a web browser because browsers pretty much just GET stuff. They don't do a lot of other types of interaction with resources. This is a problem because it has led many people to assume that HTTP is just for GETing. But HTTP is actually a general purpose protocol for applying verbs to nouns.

8. **Why can't machines understand humans?**
Because web pages are designed to be understood by people. A machine doesn't care about layout and styling. Machines basically just need the data. Ideally, every URL would have a human readable and a machine readable representation. When a machine GETs the resource, it will ask for the machine readable one. When a browser GETs a resource for a human, it will ask for the human readable one.



