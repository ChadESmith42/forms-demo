# Basic Form

We're going to create a basic form for our application. What better example than a login form? It has two inputs and a button. We could get fancy with the form, but we'll keep it simple for this demo.

First, we're going to add some structure to our app that we'll expand through the next few demos.

In the `app.component.html`, we're going to add some structure to the application. We'll start with adding a header, main, and footer tags to give our app a shape.

```html
<header>
      <h1>Form Demo Application</h1>
</header>
<main>
    <router-outlet></router-outlet>
</main>
<footer>
      <p>Coding By Chad &copy; 2022</p>
</footer>
```

I'm using HTML5 tags for the different parts of the page. This helps screen readers make the page accessible to all users. I'm also placing the `<router-outlet>` directive inside the `<main>` element. This is where our Angular content will be dynamically displayed.

If you don't know how the `<router-outlet>` directive works, take a look at the [Angular documentation for the `Router`](https://angular.io/api/router/RouterOutlet).

I also want to add a class to the `<main>` element so the footer is pushed toward the bottom of the page. I set `<main class="main">`. In the `app.component.scss`, I add the following rule:

```css
.main {
  min-height: 80vh;
}
```

This sets the `<main>` element is 80% of the view height of the DOM container.

We'll save our work and do a commit. I tag all of my commits to help identify the type of work I'm doing. You'll see tags like NEW, ADD, REFACTOR, DEL, UPDATE, and FIX. These all give context to the actual work with the fewest words possible. It helps me keep track of what I'm doing. Use whatever system works for you!

`git commit -m "ADD: app structure, basic style"`

## Adding a Login Component

Let's add a login component to our app using the Angular CLI:

`ng generate @schematics/angular:component Login --project=forms-demo --module=src/app --style=scss --path=src/app/components/forms --no-interactive`

This command does a bunch of different things. It uses the `@schematics/angular:component` template. The component will be part of the `forms-demo` project. It will be declared in the `app.module.ts`. We're setting the style to use `scss`. We're also creating the form in the `src/app/components/forms` folder. The CLI will create the `components/forms` folders for us.

This is a good place to do a commit:

`git commit -m "NEW: login component via CLI"`
