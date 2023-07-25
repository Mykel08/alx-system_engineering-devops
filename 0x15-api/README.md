Background Context


Old-school system administrators usually only know Bash and that is what they use to build their scripts. While Bash is perfectly fine for a lot of things, it can quickly get messy and not efficient compared to other programming languages. The new generation of system administrators, usually called SREs, are pretty much regular software engineers but instead of building products, they are managing systems. And one of the big differences with their predecessors is that they know more than just Bash scripting.

One popular way to expose an application and dataset is to use an API. Often, they are the public facing part of websites and micro-services so that allow outsiders to interact with them – access and modify their data. In this project, you will access employee data via an API to organize and export them to different data structures.

This is a perfect example of a task that is not suited for Bash scripting, so let’s build Python scripts.

Friends don't let friends program in shell script
Liraz Siri - Tue, 2010/02/02 - 07:38 - 2 comments
Lately I've been going over a hellish patch-work of old shell scripts we wrote to automate some internal processes and I realized something: friends shouldn't let friends program in shell script.

Why?

Shell script is ugly.
Shell script is unreliable.
Shell script doesn't have exceptions.
Shell script is hard to debug.
Shell script is hard to test.
Shell script isn't object oriented.
Shell script is full of idiosyncratic cruft.
Shell script doesn't have any decent data structures.
Shell script doesn't scale.
Shell script encourages code duplication.
The problem with shell script is that it's so deceptively easy to get started. Once you've started adding each bit of extra complexity seems easier than trashing the whole thing and starting from scratch in a decent language (e.g., Python) with a decent design.

Speaking from personal experience, nearly every time I have used shell script in recent times for something that isn't completely trivial, I have come to regret it. Ugh.

Sometimes you don't have a choice. For example, one time I had to use shell script to create a transparent command line hijacking function for a utility I was working on, and just look at the abomination I am ashamed to have been forced to write:

hijack_command() {
    CALLBACK=$1
    COMMAND=$2
    NEW_COMMAND=$3

    ORIG_COMMAND=$(which $COMMAND 2>/dev/null)

    eval "

        function $COMMAND() {
            args=()
            for arg; do
                args[\${#args[*]}]=\"'\$arg'\"
            done
            if $CALLBACK; then
                eval $NEW_COMMAND \${args[*]}
            else
                if [ \"$ORIG_COMMAND\" ]; then
                    eval $ORIG_COMMAND \${args[*]}
                fi
            fi
        }"
}

An application program interface (API) is a set of routines, protocols, and tools for building software applications. Basically, an API specifies how software components should interact. Additionally, APIs are used when programming graphical user interface (GUI) components. A good API makes it easier to develop a program by providing all the building blocks. A programmer then puts the blocks together.

In this definition...
What are Different Types of APIs?
What are Examples of Popular APIs?
Best API Management Software
WHAT ARE DIFFERENT TYPES OF APIS?
There are many different types of APIs for operating systems, applications or websites. Windows, for example, has many API sets that are used by system hardware and applications — when you copy and paste text from one application to another, it is the API that allows that to work.

Most operating environments, such as MS-Windows, provide APIs, allowing programmers to write applications consistent with the operating environment. Today, APIs are also specified by websites. For example, Amazon or eBay APIs allow developers to use the existing retail infrastructure to create specialized web stores. Third-party software developers also use Web APIs to create software solutions for end-users.

Read More: Interested in learning more about software engineering? Visit the TechRepublic Academy.

WHAT ARE EXAMPLES OF POPULAR APIS?
ProgrammableWeb, a site that tracks more than 15,500 APIs, lists Google Maps, Twitter, YouTube, Flickr and Amazon Product Advertising as some of the the most popular APIs. The following list contains several examples of popular APIs:

Google Maps API: The Google Maps API lets developers embed Google Maps on webpages using a JavaScript or Flash interface. The Google Maps API is designed to work on mobile devices and desktop browsers.
YouTube APIs: YouTube’s APIs let developers integrate YouTube videos and functionality into websites or applications. YouTube APIs include the YouTube Analytics API, YouTube Data API, YouTube Live Streaming API, YouTube Player APIs, and others.
Flickr API: The Flickr API is used by developers to access the Flick photo sharing community data. The Flickr API consists of a set of callable methods, and some API endpoints.
Twitter APIs: Twitter offers two APIs. The REST API allows developers to access core Twitter data and the Search API provides methods for developers to interact with Twitter search and trends data.
Amazon Product Advertising API: Amazon’s Product Advertising API gives developers access to Amazon’s product selection and discovery functionality. Devs can then incorporate advertisements of  Amazon products to monetize a website.
