# Using Github Actions to Publish to Nuget
Recently I needed to automate the publishing of updates to an older open source project of mine [xUnit.categories](). DotNet isn't a stack I work in much anymore, and I'd fallen behind publish updates, it was a good time to finally get github actions setup for it. 

Using [Publish NuGet](https://github.com/marketplace/actions/publish-nuget) action from the github marketplace takes care of the actual build and publish process. I was really pleased at how seemless the whole process went.

To get started you'll need to have your [nuGet api key](),

## Create a github action
To use a github action we need to create a `.github/workflows` directory. Then Inside that directory create a `publish.yml` file for the action. 


> `.github/workflows/publish.yml`

Next copy the yml contents from the [Usage](https://github.com/marketplace/actions/publish-nuget#usage) linked here and paste them into your `publish.yml` 

The first section gives your actions name, then the `on` section defines how the action will be triggered. I chose to have each merge into the `master` branch to update the nuget package. The default settings have this already configured, there are other events that can [trigger actions](https://docs.github.com/en/actions/reference/events-that-trigger-workflows). 

```yml
name: publish to nuget
on:
  push:
    branches:
      - master # Default release branch
```



Use the guys existing action
- trigger type
- package info


Add Secret

.csproj 



