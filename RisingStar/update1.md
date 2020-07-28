
Hi, my name Brendan Connolly and I am the 2019 Rising Star Award winner. I wanted to introduce you to my concept, inclusive automation and share a little why I think it is so important for the testing community. Then we'll sneak a peak at one of the core pieces o tech,  Jupyter Notebooks that I think with help of the supoorters can really change the way we percieve, value and consume automation as testers.

Automation is currently highly exclusionary activity. It excludes tests that don’t fit well into the confines of headless execution. It excludes testers that cannot code.  It excludes validating the monitoring and observability data that teams are increasingly relying upon. This encourages a class divide between “manual” testers and SDETs or automation engineers. This all results in an environment that treats testing as a binary, automated(good) or manual(bad).

There are many highly skilled testers out ther, some can code but many can not, this doesn't mean they aren't adding value to their teams. 

The continuous pressure to upskill testers into automators can take a toll on people.  It also creates a hierarchy that often devalues a testers skills and contributions to teams. 

What I am hoping is that with this idea  and the help of the supporters, we can start to create a mindshift around automation. Fostering a healthier and more robust approach to automated testing that is inclusive of the diverse range of skills that testers bring to their teams. 

To help bridge the gap between automated and manual tests I have been using Jupyter Notebooks. These notebooks are very popular in the data science world, but I believe they are a powerful tool for integrating automation into exploratory testing. 

This notebook is just a sample so you can get a sense of what they are and how they can start being used while testing. 
In this case I am using ruby and capybara to book a room at a bed and breakfast website.

A notebook is comprised of a set of cells. A cell can hold executable code or markdown for descriptive text, links etc. 

The first cell is code cell that includes a file that wires up selenium for use inside the notebook. To execute this step I click the run button.

Next is a markdown cell that provides a description of the purpose of the notebook.

Stepping through the notebook, we navigate to the site and 

you can see we have a note here to click through any of the initial prompts, to chose a room to book. Initially this calendar control seems a bit tricky to automate so we'll do that manually as well. 

these next 2 cells have code setup the test data and fill in the form. 

Running them you can see the form is filled in with our values. You can also see that using this take screenshot method renders the actual screen shot directly inside the notebook. So as we start testing we are building a living artifact that we can use to track testing notes and share with team members or export to pdf and attatch to work items.

Continuing through the notebook, we'll try to complete the room booking.


Looks like the phone number is too short. Depending on your context and its needs you have a couple options here. We can go back to these cells, update the phone number value and re-run them. 

Or we can add new cells to document our actions. Wer can copy past the code cells or we can note a manual step and take a screenshot. 

The important thing here is that the tester is the one in control. The browser is up and available for automation but it is equally available for exploration. 

This is really just the tip of the iceberg, now  that we accept a different modality for automation we can start layering in things that never would have been viable in traditional headless fully automated tests.

Things that we as skilled human testers could benefit from. We can intergrate external services, check analytics, monitoring error reporting logging. 
The notebook starts to represent a mopre holisitic picture of the testing 

So stay tuned, I'll be working with the supporters to refine and improve these ideas and provide a set of resources and content throughout the upcoming year to try and make automation a more inclusive space for all testers