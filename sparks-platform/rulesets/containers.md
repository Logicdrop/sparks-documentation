# Containers

## Running a Container

The container is one of the most important concepts in the Sparks Platform Rule services. A container represents the executable endpoint exposed for usage. 

One or more containers can be running at any given time. For example, you may have a production container running and another container that you are working on the next iteration running.

![](https://lh4.googleusercontent.com/z3doKoNR9DBTA-grBl1n6m3rcKQTyYV618AgnW2QJyiFQ893O-Hp3Us8rGaGydD2PGjJ2hvm1x5NG9RK042kL7pizpN4aXK4q_8dEVh4kxA5WmIO5szqNJwRX05VG5OGxq_Z5WBR)

Containers can be in one of three states:

* **Running** \(green check mark\) means the container has started successfully and is running. You can access it through the API or the testing screen.
* **Stopped** \(red square\) means the container has been stopped. Stopped containers cannot be accessed externally and testing functionality will not work until they are started again.
* **Error** \(red exclamation\) means the container did not start properly and hence, is not running. Containers will be in this state most likely due to error\(s\) in rules or types.

On any container the actions that can be performed are \(far right of the container item view\) Publish, Start, and Stop.

#### **To Publish** \(rebuild\) a new or updated container

Click on the Publish button to rebuild and start the container because the ruleset has changed. If you have made changes to a ruleset that you want to expose or test you must publish the container first. This is the equivalent of stop/rebuild/run.

#### **To start** a stopped container

Click on the Run button to start a manually stopped already existing container. This does not rebuild the container,  it uses the last known good build. You generally will run a previously manually stopped container.

#### **To stop** a running container

Click on the Stop button to pause or disable a running container if you do not want anyone to access your container or it is a work in progress and only you or a few collaborators use it occasionally.

## Common Problems

### Container Does Not Start

One of the most frequent problems that will occur, and prevent a container from starting, are compilation errors in the rules.

When getting started with a ruleset, this can be the most tedious and time consuming process. It requires manipulating the ruleset \(rules, types, content, etc.\), publishing the container, looking at the errors, and repeating the process until the container starts.

Problems that typically occur, especially in the beginning, are:

* Missing types or properties
* Improper syntax in the the ruleset content or user rules
* Typo’s \(address vs. adress and expecting address in the rules\)

If an error occurs you will need to publish the container until it successfully starts. Rebuilding recreates and validates the ruleset from scratch each time. 

{% hint style="info" %}
Note that if publishing is not successful, the last "good" version of that container will automatically continue to exist and run when started/stopped. The container only updates with new rules when publishing finishes without errors.
{% endhint %}

The process to work with rules until a container is successfully starts follows a sequence like below:

1. Publish the container because this is a new ruleset or there are changes you want reflected. 
   1. Did the container fail to start because of errors? ![](https://lh3.googleusercontent.com/uKmVoHNNbOgfM_DUOwlOskX_MQLcQyMtvvjVEYKXF8gZeHPMD0Wbob2ZMha2BMmgIrjt2dl2-OEWXPNmqgyir62mQ9dZfnj32ts-7zdiGHqHux8-_x2l0RHTyi3w4pwNKxp6xAL3)  
2. Inspect the errors. 
   1. In the “error” message you can click Generate Ruleset Code and try to approximate where the line\# vs. the error is. ![](https://lh6.googleusercontent.com/fPg45TQYiSIlq9F8kqo4oqCsfqNMbpYfZcddjUUeyUMWGLbsymRXWQniFI8BnBIXmzLql91YhhQCdPh3-b9FJUeOWoyyoXJR0aNT7WlWf1h1XlxLWVxD1FRHkul895Sc2L4rMmpA) 
   2. Look at any changes you may have just made. If the container was running before there is a high likelihood something recently introduced caused the error. 
3. Make changes to the ruleset and save. 
4. Publish the container - did it fail to start?  Repeat the process above until it starts.

{% hint style="info" %}
**Pro Tip:** Because of the amount of detail needed when designing, debugging, and testing rules it can be much easier if you have separate tabs open for containers and the ruleset editor.
{% endhint %}

