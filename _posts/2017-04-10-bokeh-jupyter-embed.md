--- 
layout: post 
title: Embedding Bokeh Applications within Jupyter Notebooks
tags:
- bokeh
- python
- pandas
--- 

With the recent release of Bokeh version [0.12.5](https://bokeh.github.io/blog/2017/4/5/release-0-12-5/), you can now embed Bokeh applications within Jupyter Notebooks.  You can therefore more easily prototype your Bokeh applications within Jupyter, for eventual transition into Bokeh server applications or flask-based applications.

To illustrate the new functionality, I have put together a simple "Hello, World" application using the Iris data set, one of the most commonly used data sets in machine learning.  The application enables users to select a feature (Sepal Length, Sepal Width, Petal Length, or Petal Width) via a pull-down menu, and automatically displays a color-coded histogram for the chosen feature.  A screenshot of the application is shown below:

![Bokeh Jupyter Embed](https://raw.githubusercontent.com/ecerami/ecerami.github.io/master/img/bokeh-jupyter-embed.gif)

You can download the [notebook on github](https://github.com/ecerami/pydata-essentials/blob/master/bokeh/bokeh_notebook_embed.ipynb), or clone the [entire project](https://github.com/ecerami/pydata-essentials).

A few important points to note:

First, this will only work in the latest version of bokeh.  If you are using pip, first make sure to run: `pip install -U bokeh`.  

Second, to set up your application, run:

    handler = FunctionHandler(modify_doc)
    app = Application(handler)

The first line sets up a `FunctionHandler` with a local method that defines your application document.  Within this function, you define your plots and controls.  In my case, I am using a color-coded[Histogram plot](http://bokeh.pydata.org/en/latest/docs/reference/charts.html#histogram "Histogram plot") and a single [Select ](http://bokeh.pydata.org/en/latest/docs/reference/models/widgets.inputs.html "Select")widget.  Additionally, when a user selects an option from the drop-down menu, the `update() `method is called.  The second line initializes your application within a Python [Tornado](http://www.tornadoweb.org/en/stable/ "Torndao") server, automatically wrapped by Bokeh.

Third, although not strictly necessary, I found it helpful to create the application document explicitly:

	doc = app.create_document()

This aids in debugging your application.  Otherwise, the application document is created within Tornado, error messages are hidden from view, and you will not see any output.

Finally, once your application is set-up, you can embed the application within Jupyter:

	show(app, notebook_url="localhost:8888")

One small gotcha here is that the `notebook_url` parameter must match the port of your Jupyter notebook server.  If you specify a different URL, you will not see any output.

I hope this is helpful.  Let me know what you think!
