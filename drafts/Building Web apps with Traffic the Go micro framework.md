#Building web apps with Traffic, the Go micro framework.  

Micro frameworks are undoubtly on the rise.   
Their *make-no-assumption-on-what-I-need* policy and the smooth learning curve are one of the keys of their success.  

But why are really micro frameworks so popular?   
The author of [this article][2] makes a point explaining why a freshman developer should not learn Rails first (ora any other full fledged framework), but should start by learning [Sinatra][3], the Ruby micro framework, instead.  
His point is very clear: micro frameworks are easier to learn and get productive with, while maintaining full control on what's going on behind the curtains.    
According to the article, to create an *"Hello World"* application in ROR you need 51 files, while with Sinatra only 1. The content of one file is the exact size of a developer's memory buffer.  
Another interesting read is the definition of [*micro*][4] on the Flask website (  
Flask is another popular micro framework in *Python*).  
Trending keywords are **easy**, **concise** and **extensible**.

There's also one last reason: software development is moving towards creating services for other applications and micro frameworks serve very well this paradigm by providing an easy way to create the building blocks, such as a REST API, on top of which larger applications rely.  

Micro frameworks do not cover every single aspect of applciation building, most of them are left to the developer, for example you decide which database to use and how to access it or not to use a DB at all, while they provide all the basic tools needed to create and maintain an appllication.

Following the path of Sinatra, long time Ruby developer [Andrea Franz][1] wrote [**Traffic**][5], a small framework for Web development in Go.  

Like many other popular frameworks Traffic basic features include

- regexp routing 
- chainable request filters
- middlewares
- templates
- serving of static files
- custom error handlers
- facilities to render in various format (HTML, JSON and XML)
- errors and stacktraces in the browser
- command line utility to generate new projects (although very basic)

We are going to analyze each one of them, by writing a small demo application.  
The application is a clone of the [placehold.it][6] service, but with the 
Grumpy cat in place of gray boxes.  
We named it ***Purrraceholder*** (read it with a japanese accent) and, as usual, code is
available on [github][7].

###Installing Traffic  
Assuming you already have a working installation of Go, download Traffic   

`go get github.com/pilu/traffic`

and the command line tool  

`go get github.com/pilu/traffic/traffic`

create a new project

`traffic new demo_project`

run it

	cd demo_project  
	go build && ./demo_project

and point your browser to [http://127.0.0.1:7000/](http://127.0.0.1:7000/)
	



```
w.Header().Set("Access-Control-Allow-Origin", "*")
```

[1]: http://gravityblast.com/
[2]: http://www.samanthajohn.com/post/17643298219/dont-learn-rails
[3]: http://www.sinatrarb.com
[4]: http://flask.pocoo.org/docs/foreword/#what-does-micro-mean
[5]: https://github.com/pilu/traffic/
[6]: http://placehold.it/
[7]: https://github.com/wstucco/purrraceholder