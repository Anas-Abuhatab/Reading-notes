
# How I explained REST to my brother

Brother: Hey, I have a question for you… Who is “Roy Fielding”?

ME: Some guy. He's smart.

Brother: Oh? What did he do?

ME: He helped write the first web servers, that sent documents across the internet… and then he did a ton of research explaining why the web works the way it does. His name is on the specification for the protocol that is used to get pages from servers to your browser.

Brother: How does that work, anyway?

ME: The web?

Brother: Yeah.

ME: Hmm. Well, it's all pretty amazing really. And the funny thing is that it's all very undervalued. The protocol I mentioned, that he helped write, HTTP, it's capable of all sorts of neat stuff that people ignore for some reason.

Brother: You mean “http” like the beginning of what I type into the browser?

ME: Yeah. That first part tells the browser what protocol to use. That stuff you type in there is one of the most important breakthroughs in the history of computing.

Brother: Why?

ME: Because it is capable of describing the location of something anywhere in the world from anywhere in the world. It's the foundation of the web. You can think of it like GPS coordinates for knowledge and information.

Brother: For web pages?

ME: For anything really. That guy, Roy Fielding, he talks a lot about what those things point to in that research I was talking about. The whole world wide web is built on an architectural style called “REST”. REST provides a definition of a “resource”, which is what those things point to.

Brother: A web page is a resource?

ME: Kind of. A web page is a “representation” of a resource. Resources are just concepts. URLs--those things that you type into the browser...

Brother: I know what a URL is.

ME: Of course. Those URLs tell the browser that there's a concept, somewhere. A browser can then go ask for a specific representation of the concept. Specifically, the browser asks for the web page representation of the concept.

Brother: What other kinds of representations are there?

ME: Actually, representations is one of these things that doesn't get used a lot. In many cases, a resource has only a single representation. But we're hoping that representations will be used more in the future because there's a bunch of new formats popping up all over the place.

Brother: Like what?

ME: Hmm. Well, there's this concept that people are calling “Web Services” or "APIs". It means a lot of different things to a lot of different people but the basic concept is that machines could use the web just like people do.

Brother: Is this another robot thing?

ME: No, not really. I don't mean that machines will be sitting down at the desk and browsing the web. But computers can use those same protocols to send messages back and forth to each other. We've been doing that for a long time but none of the techniques we use today work well when you need to be able to talk to all of the machines in the entire world.

Brother: Why not?

ME: Because they weren't designed to be used like that. When Fielding and his colleagues started building the web, being able to talk to any machine anywhere in the world was a primary concern. But most of the techniques developers later used to get computers to talk to each other didn't have those requirements. You just needed to talk to a small group of machines.

Brother: And now you need to talk to all the machines?

ME: Yes - and more. We need to be able to talk to all machines about all the stuff that's on all the other machines. So we need some way of having one machine tell another machine about a resource that might be on yet another machine.

Brother: What?

ME: Let's say you're talking to our sister and she wants to borrow Great Grandma's silver water jug or something. But you don't have it - Mom has it. So you tell our sister to get it from Mom instead. This happens all the time in real life and it happens all the time when machines start talking too. On the internet, it's called a "redirect".

Brother: So how do the machines tell each other where things are?

ME: Ah! With a URL. If everything that machines need to talk about has a corresponding URL, you've created the machine equivalent of a noun. That you and I and the rest of the world have agreed on talking about nouns in a certain way is pretty important, eh?

Brother: Yeah.

ME: Machines don't have a universal noun - that's why they suck. Every programming language, database, or other kind of system has a different way of talking about nouns. That's why the URL is so important. It let's all of these systems tell each other about each other's nouns.

Brother: But when I'm looking at a web page, I don't think of it like that.

ME: Nobody does. Except Fielding and handful of other people. That's why machines still suck.

Brother: Ha, what about verbs and pronouns and adjectives?

ME: Funny you asked because that's another big aspect of REST. Well, verbs are anyway.

Brother: I was just joking.

ME: Well done! but it's actually not a joke at all. Verbs are imp

