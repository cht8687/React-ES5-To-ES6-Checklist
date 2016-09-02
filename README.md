ES6 and beyond is very popular.

> JS is also unlike any other language in that the experimentation occurs on massive scale thanks to transpilers. Never happened before. -- Dan Abramov

[React](https://github.com/facebook/react) is a declarative, efficient, and flexible JavaScript library for building user interfaces.

In the earlier days of React development, many programms were written in ES5. Howerver, as ES6 and beyond is more widely accepted now and with the help of transplier tools like [Babel](https://github.com/babel/babel), we can gradually retire some ES5 code and adopt some new JavaScript features in React development. 

Here is a check list to help you translate your ES5 code to ES next in React.
You are welcome to contribute with more items provided below.

## Quick links

1. [require => import](#require)
1. [createClass => extends React.Component](#createClass)
1. [module.exports => export default](#module)
1. [name function()  =>  name()](#name)
1. [getDefaultProps and propTypes](#getDefaultProps)
1. [getInitialState](#getinitialstate)
1. [destructuring & spread attributes](#destructuring)
1. [use arrow functions](#use)

### <a id="require"></a>require => import

ES5

  ```js
  //ES5
  var React = require("react");  
  var PropTypes = React.PropTypes;
  ```

ES6

  ```js
  import React, { Component, PropTypes } from 'react';
  ```

**[⬆ back to top](#quick-links)**

### <a id="createClass"></a>createClass => extends React.Component

ES5

  ```js
  var Mycomponent = React.createClass({
    render: function() {
      return (
        <div>ES5</div>
      );
    },
  });
  ```

ES6

  ```js
  class Mycomponent extends React.Component {
    render() {
      return (
        <div>ES6</div>
      );
    }
  }
  ```
**[⬆ back to top](#quick-links)**

### <a id="module"></a>module.exports => export default

ES5

  ```js
  var Mycomponent = React.createClass({
    render: function() {
      return (
        <div>ES5</div>
      );
    },
  });

  module.exports = Mycomponent;

  ```

ES6

  ```js
  export default class Mycomponent extends React.Component {
    render() {
      return (
        <div>ES6</div>
      );
    }
  }
  ```
**[⬆ back to top](#quick-links)**

### <a id="name"></a>name function()  =>  name()

ES5

  ```js
  var Mycomponent = React.createClass({
    componentWillMount: function(){

    },
    render: function() {
      return (
        <div>ES5</div>
      );
    },
  });

  module.exports = Mycomponent;

  ```

ES6

  ```js
  export default class Mycomponent extends React.Component {
    componentWillMount() {

    }
    render() {
      return (
        <div>ES6</div>
      );
    }
  }
  ```

**[⬆ back to top](#quick-links)**

### <a id="getDefaultProps"></a>getDefaultProps and propTypes

ES5

  ```js
  var Video = React.createClass({
      getDefaultProps: function() {
          return {
              autoPlay: false,
              maxLoops: 10,
          };
      },
      propTypes: {
          autoPlay: React.PropTypes.bool.isRequired,
          maxLoops: React.PropTypes.number.isRequired,
          posterFrameSrc: React.PropTypes.string.isRequired,
          videoSrc: React.PropTypes.string.isRequired,
      },
      render: function() {
          return (
              <View />
          );
      },
  });
  ```

ES6

  ```js
  class Video extends React.Component {
    render() {
        return (
            <View />
        );
    }
  }
  Video.defaultProps = {
      autoPlay: false,
      maxLoops: 10,
  };
  Video.propTypes = {
      autoPlay: React.PropTypes.bool.isRequired,
      maxLoops: React.PropTypes.number.isRequired,
      posterFrameSrc: React.PropTypes.string.isRequired,
      videoSrc: React.PropTypes.string.isRequired,
  };
  ```

ES future proposals:

  ```js
  class Video extends React.Component {
    static defaultProps = {
      autoPlay: false,
      maxLoops: 10,
    }
    static propTypes = {
      autoPlay: React.PropTypes.bool.isRequired,
      maxLoops: React.PropTypes.number.isRequired,
      posterFrameSrc: React.PropTypes.string.isRequired,
      videoSrc: React.PropTypes.string.isRequired,
    }
    state = {
      loopsRemaining: this.props.maxLoops,
    }
  }
  ```

**[⬆ back to top](#quick-links)**

### <a id="getInitialState"></a>getInitialState

ES5

  ```js
  var Header = React.createClass({
    getInitialState: function() {
      return {
        title: this.props.title
      };
    },
  });
  ```

ES6

  ```js
  export default class Header extends Component {
    constructor(props) {
      super(props);
        this.state = {
          title: props.title
        };
      }
  }
  ```

ES future proposals:
  
  ```js
  export default class Header extends Component {
    state = {
      title: this.props.title
    };
      
    // followed by constructor...
  }
  ```

**[⬆ back to top](#quick-links)**

### <a id="destructuring"></a>destructuring & spread attributes

```js
class AutoloadingPostsGrid extends React.Component {
  render() {
    var {
      className,
      ...others,  // contains all properties of this.props except for className
    } = this.props;
    return (
      <div className={className}>
        <PostsGrid {...others} />
        <button onClick={this.handleLoadMoreClick}>Load more</button>
      </div>
    );
  }
}

```

**[⬆ back to top](#quick-links)**

### <a id="use"></a>use arrow functions

Stateless component:

```js

function App() {
  return (
    <div>
      <MyComponent />
    </div>
  );
}

```

Using Arrow function:

```js
const App = () => (
  <div>
    <MyComponent />
  </div>
);
```

Using Arrow funtion with [Destructuring function arguments](https://github.com/getify/You-Dont-Know-JS/blob/master/es6%20&%20beyond/ch2.md#destructuring-parameters):

```js
const App = ({className, ...rest}) => (
  <div className={classnames(className)} {rest}>
    <MyComponent />
  </div>
);
```

**[⬆ back to top](#quick-links)**

## Reference

* [React](https://github.com/facebook/react)
* [Babel](https://github.com/babel/babel)
* [ECMAScript 6 support in Mozilla](https://developer.mozilla.org/en/docs/Web/JavaScript/New_in_JavaScript/ECMAScript_6_support_in_Mozilla)
* [React on ES6+](https://babeljs.io/blog/2015/06/07/react-on-es6-plus)
* [Converting React project from ES5 to ES6](http://cheng.logdown.com/posts/2015/09/29/converting-es5-react-to-es6)
* [React/React Native 的ES5 ES6写法对照表](http://bbs.reactnative.cn/topic/15/react-react-native-%E7%9A%84es5-es6%E5%86%99%E6%B3%95%E5%AF%B9%E7%85%A7%E8%A1%A8/2)

## Roadmap

- [ ] Include all ES5 to ES6+ instructions for React
- [ ] We may Implement ESlint plugin like ESlint-Plugin-React-5-to-6
- [ ] We may Include instructions for configuring Babel with different stages

# License

MIT
