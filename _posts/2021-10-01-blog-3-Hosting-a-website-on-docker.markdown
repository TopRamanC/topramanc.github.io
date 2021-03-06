---
layout: post
title:  "Blog 3 - Hosting a website on Docker"
date:   2021-10-07 18:0:20 -0700
categories: jekyll update
---

# **What do you need to host a website on Docker?**
* Docker installed
* A Dockerfile
* Your html file

# **What is a Dockerfile?**
#### A Dockerfile consists of commands and instructions that are used to build a docker image. Dockerfile helps automate the process of building an image by executing multiple commands.

# **What should your Dockerfile contain to host a web server?**
#### Your Dockerfile must contain the Apache httpd server along with your html file to be hosted.

# **Below is a walkthrough of how to host and test your website:**

# **First we need to create our Dockerfile:**
{% highlight ruby %}
FROM httpd  # This line obtains an image for the Apache web server

WORKDIR /usr/local/apache2/htdocs # Set the correct working directory

COPY index.html . # Copy our html file into the working directory
{% endhighlight %}

# **Docker commands needed to host your website:**
#### The command below will create a custom image from our Docker file and tag it "my_image":
{% highlight ruby %}
 Docker build -t my_iamge .
{% endhighlight %}

#### The command below will run a container from the custom image we created in the last step and connects port 8080 with the local machine port 8080:
{% highlight ruby %}
 Docker run -dit --name my_website -p 8080:8080 my_image
{% endhighlight %}

# **Congrats!! Now you have succesfully deployed your website but how can you check validate if everything is running correctly?**
#### There are two ways to make sure our webpage is running correctly:
* You can curl http://localhost:8080/ on your machine.
{% highlight ruby %}
<!DOCTYPE html>
<html>
    <head>
        <title>Hello World!</title>
    </head>
</html>
{% endhighlight %}

* You can visit the url http://localhost:8080/ on your browser.
  ![Commands Image](https://topramanc.github.io/Images/hello-world.png)