

## What are Jupyter Notebooks

Jupyter Notebooks are web based documents that blend together [markdown](), code that can be executed on the fly as well as visual output of that codes results.  

They have gained immense popularity in data science and academia. The code to manipulate data can live side by side with the resulting visualization and an explanation for how it should be interpreted. What makes it even more powerful code is editable and executable in real time by the viewer, so the full story of the code can come to life right in front of their eyes.

### Multi-Language Support

Jupyter requires and runs on Python but don't let that fool you, it supports over [40 different languages](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels) including JavaScript, Ruby, Java, C#.  Language support is provided through a concept called [kernels](https://jupyter.readthedocs.io/en/latest/projects/kernels.html) which enables the Jupyter user interface to hand off the code execution to language specific engines. 

Each notebook is created targeting a specific language kernel, 

## Why with Selenium?

This all sounds very interesting and all, but why use a tool for data scientists and academics for software testing?

### For Authoring
As test automation efforts on teams grow and mature, the automation frameworks the get built tend to optimize for the headless execution of tests. It makes sense, its faster and less intrusive to run tests without having the application popup into view and take over your machine as it runs through the application under test. 

When writing a test though your needs are different and sometimes at odds with this focus on isolated, and invisible invisible testing. It's a visually intensive process to see how the actions and selectors you are using are actually working.

Test authoring requires you to step through the workflow and sometimes repeatedly try just a few lines of a test multiple times. 

Mistakes or the fun nuances in products you find when attempting to automate them mean you need different selectors, a different wait strategy, or any number of other things that result in needing to re-execute the test.

In traditional test authoring you would re-run the test, maybe with the debugger and a few break points set. This means wait for any test data setup to complete, spin up the browser and then wait for your test to get to the lines you need to work on. Even if this is fairly fast it still breaks up your feedback loop.

Using Jupyter Notebooks each cell is editable and can be independently executed multiple times. This means you can additively 

### Semi-Automating

### For Exploring



## Dependencies

Kernels
[IRuby](https://github.com/SciRuby/iruby)
