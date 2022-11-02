# Material UI responsive

# Breakpoint

- **Default breakpoint**

```yaml
    xs, extra-small: 0px
    sm, small: 600px
    md, medium: 900px
    lg, large: 1200px
    xl, extra-large: 1536px
``` 

- **Css Media queries**

```js

    theme.breakpoints.up(key)
    theme.breakpoints.down(key)
    theme.breakpoints.only(key)
    theme.breakpoints.not(key)
    theme.breakpoints.between(start, end)

``` 

```js
import * as React from 'react';
import { styled } from '@mui/material/styles';
import Typography from '@mui/material/Typography';
import { red, green, blue } from '@mui/material/colors';

const Root = styled('div')(({ theme }) => ({
  padding: theme.spacing(1),
  [theme.breakpoints.down('md')]: {
    backgroundColor: red[500],
  },
  [theme.breakpoints.up('md')]: {
    backgroundColor: blue[500],
  },
  [theme.breakpoints.up('lg')]: {
    backgroundColor: green[500],
  },
}));

export default function MediaQuery() {
  return (
    <Root>
      <Typography>down(md): red</Typography>
      <Typography>up(md): blue</Typography>
      <Typography>up(lg): green</Typography>
    </Root>
  );
}


```

- **Custom media queries**
```js

const theme = createTheme({
  breakpoints: {
    values: {
      xs: 0,
      sm: 600,
      md: 900,
      lg: 1200,
      xl: 1536,
      mobile: 0,
      tablet: 640,
      laptop: 1024,
      desktop: 1200,
    },
  },
});


declare module '@mui/material/styles' {
  interface BreakpointOverrides {
    xs: false; // removes the `xs` breakpoint
    sm: false;
    md: false;
    lg: false;
    xl: false;
    mobile: true; // adds the `mobile` breakpoint
    tablet: true;
    laptop: true;
    desktop: true;
  }
}


```

- **Manage style breakpoint**
```js 

const styles = (theme) => ({
  root: {
    backgroundColor: 'blue',
    // Match [md, md + 1)
    //       [md, lg)
    //       [900px, 1200px)
    [theme.breakpoints.only('md')]: {
      backgroundColor: 'red',
    },
  },
});

```
