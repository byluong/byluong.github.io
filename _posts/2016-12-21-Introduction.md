---
title: "Better late than never"
---
# Hi, I'm Brandon.
I'm a third year Computer Science major at UC Davis.  
I'm president of [Theta Tau](http://www.davisthetatau.com/) (a co-ed professional engineering fraternity).  
I love gaming, coding, watching anime, and my cat [Marla](http://vsco.co/basedgiraffe/media/57aa64368da933c44f8b456a).  
In my spare time I dabble in [graphic design](https://photos.google.com/share/AF1QipPZDcic5RhNqlu19qRLeRA6rbw6mYtzR9DqAo0Gn-SKw3AAIPuFg0V2stjN4sUJ2w?key=Q2dMOF83bnFJLVhkT0tUVzYzTFdHWkJRWFFYWjdR), [film](https://www.youtube.com/watch?v=qnBEv72tgNQ), and [photography](http://vsco.co/basedgiraffe/).  

### In the past, I've been:  
Network Infrastructure Analyst Intern @ [Accenture](https://www.accenture.com)  
Technical Consultant @ [Luong MD](https://www.zocdoc.com/doctor/lien-luong-md-28398)  
Scribe @ [Theta Tau](http://www.davisthetatau.com/)  
Webmaster @ [Theta Tau](http://www.davisthetatau.com/)  
Public Relations Chair @ [Theta Tau](http://www.davisthetatau.com/)  
Historian @ [Theta Tau](http://www.davisthetatau.com/)  

Peek at my [code feed](/code/), look at my [portfolio](/portfolio/), or check out [my graphic design work](/visuals/).  

<div class="grid__wrapper">
  {% for post in site.portfolio %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
  {% for post in site.visuals %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
<!-- {% include figure image_path="/assets/images/splash.jpg" caption="(I'm on the right)"%} -->