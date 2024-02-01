# iis-config-react-router
The configuration file required for IIS to use a react application using react-router and being able to navigate to all your routes.

There's a Subdomain branch that uses a bit different config file required for when deploying on subdomains  (i.e your-app-url.com/subdomain)


**Deployment Tips for React Application using react-router with Vite on IIS.**

Build your browser router with a basename if you're deploying on a subdomain. 
Below example works for all kinds of routes, default & subdomains.

```const router = createBrowserRouter(
    createRoutesFromElements(
        <>
            <Route path='/' element={<RootLayout />} errorElement={<ErrorPage />} loader={RootLoader}>
                //Add your routes here
            </Route>
        </>
    ), { basename: `${import.meta.env.BASE_URL}`}
)
```

Build your project using `npx vite build`. 
If you deploy in a subdomain, use `npx vite build --base=/subdomain`

Add the web.config file inside your IIS directory (Next to index.html). 

You should now be able to navigate to all your routes.
