# fuze-boilerplate

This is a demonstration of extending a legacy app developed with an "old" framework (in this example, angularJS) with new modules created in modern frameworks.

This tutorial will show how to use the micro-frontends approach to extend a large-scale application with new features developed in new standards, with minimal integration effort and no need to rewrite the whole application.

This enables developers and project managers to reduce cost and effort over time under the heavy dome of the "javascript fatigue".

We should focus on feature development, not feature rewrite.

In the following demo we will use `microfronts` as the supporting library for orchestrating multiple front-ends and `lerna` as our task runner. The project's folder structure in this example will be `mono-repo` style, as this is not mandatory - it is easier to work with.

Read more here:
- [lerna](https://lerna.js.org/)
- [microfronts](https://github.com/eavichay/microfronts)

#usetheplatform

## Step 1
Place the legacy application under "packages".
For the example we will take our "legacy" application from the RealWorldApp project's angularJS implementation (https://github.com/gothinkster/angularjs-realworld-example-app).
- `cd packages/conduit`
- `git clone git@github.com:gothinkster/angularjs-realworld-example-app.git .`

## Step 2
Create the shell application and orchestrate the legacy app to work as-is.
- `cd packages/shell`
- create `src/index.html` file with simple html structure
- create and empty `src/index.js`
- embed the `src/index.js` file into the `src/index.html` file.

## Step 3
Add a new module under a new url route, created in a different framework.
- `cd packages/todos`
- create a react boilerplate app. For the example we will use `create-react-app`

## Step 4
Integrate between the modules to work as one.
- Configure the shell
- Configure the new routes
- Disable "unknown" routes on legacy modules
- Enable shared runtime between the modules
- And more...

### Micro-fronts development requirements and planning
- Know your project. There are obstacles towards the full integration.
- Enable CORS for your dev-servers. Microfronts assumes you are working with "friendly-frames", meaning CORS enabling is crutial. For deployment there are various approaches, this will be discussed in the fuze.
- Be familiar with your current routing mechanism. Some routers enforces prefixes, or provide default fallback to a specific route. This should be handled. In this demo we will deal with the "legacy" app's router and enable it to work with other modules.
- Build and deployment. Every project needs it's own practice. Projects can be deployed on multiple servers and accessed via reversed-proxy, or be deployed on same endpoint with different folder prefixes. All apply.
- Plan your routes, how your screens should look for each of them. Some may have only 1 visible module at a time, some can be displayed side-by-side with full integration. Prepare your basic blueprints before we start working on your project.
- Refactoring: Some services can be easily refactored as a common code. Some can be provided and shared between modules at runtime. The best practice is to pull business-logic out of the framework, but this can be done step-by-step. The idea is to go forward while adding new features and choose which refactors can be dealt later, or not at all.

## Step 5...
Add more modules with different frameworks.

## Extended topics (TDB):
- Sharing common code at runtime
- Sharing assets (3rd party code, stylesheets, images, fonts, etc.)
- Uniform build and deployment