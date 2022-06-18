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

## Navigation

We'll also need to navigate to our login form. Let's create a Header Component that will hold the navigation and make life easier as we go through this demo.

Using the same Angular CLI, we'll create a new component.
`ng generate @schematics/angular:component Header --project=forms-demo --module=src/app --style=scss --path=src/app/components --no-interactive`

We'll commit these changes as well before we continue.

`git commit -m "NEW Header Component via CLI"`

Let's replace the `<header>` content with our new `HeaderComponent`.

```html
<header>
  <app-header></app-header>
</header>
```

### Add Content to the Header

Let's add the navigation to our header. We'll start with just the basics and add more as we go.

```html
<!-- In header.component.html -->
<section>
  <h1>Forms Demo Application</h1>
</section>
<nav>
  <a class="nav-link" routerLink="/login" routerLinkActive="active" ariaCurrentWhenActive="page">Login</a>
</nav>
```

Let's add some styling, so it looks a little more readable.

```scss
/* In header.component.scss */
nav {
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-evenly;

  .nav-link {
    flex: 0 1 auto;
    padding: .75rem 1rem 1rem 1rem;
  }
}
```

I've set my `<nav>` element to use flex-box and display the items in a row. The content should not wrap and will be evenly spaced.

I've added just a touch of padding to each `.nav-link` element. This should help keep things visually appealing.

Let's add the routing so we can work with our form.

```ts
//  In app-routing.module.ts

const routes: Routes = [
  { path: 'login', component: LoginComponent }
];
```

This creates a route for the `LoginComponent`. We could make it the default or use other options to make this realistic (like a resolver or routeGuard). Those are beyond the purpose of this demo.

Let's commit and save our work. For this section, I'm committing the changes to the `HeaderComponent` and the `AppRouting` separately. This helps if we need to revert changes (we won't but it's a good habit to develop).

For the changes to `app.component.html` and `header.component.html`, we'll use this:

`git commit -m "ADD: header content"`

For the changes to `app-routing.module.ts`, we'll use this:

`git commit: -m "Add: route for login"`

## The Form Already
