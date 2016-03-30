Sources: {
http://blog.teamtreehouse.com/react-hype-real
https://www.linkedin.com/pulse/what-reactjs-why-i-recommend-other-javascript-sandip-das
http://facebook.github.io/react/docs/getting-started.html
}

History:
     -built by FB developers (2013)
     -why: To build large app w/ data that changes over time
     - released as open source project

Who uses it
     - facebook
     - instagram

What is it
- Javascript library for building user interfaces
- View in MVC ( making awesome views that updates in real time!)
- anytime data changes, react only updates the changed parts ( MAGIC! )
- focuses on reusable component!!
- Unidirectional flow of data

CONCEPTS :
- React Element :
     - JS object that represent HTML elements
     - do NOT exit in browser

*** Components*** :  (STAR PLAYER!! MVP award!!)
     - react element that developers create (custom react element)
     -use method to create custom component class

Rendering :
     - virtual element ( element or component)
     - exist in JS memory
               - accepts 2 argument (virtual element and real DOM node)
                    (1.) react make the virtual element and (2.) insert it to the real DOM NODE

Property (props) :
     - gives as argument to component
               - looks like HTML attributes
     - attribute available in components and can be used in render method to render dymnaic data
     -  component should never change its props, they're immutable. If a component has data that's mutable, use             the state object.

State:
     - state object is internal to a component
     - holds data which can change over time.
     - State is set using the method & calling it triggers UI updates
var Photo = React.createClass({

  toggleLiked: function() {
    this.setState({
      liked: !this.state.liked
    });
  },

  getInitialState: function() {
    return {
      liked: false
    };
  },

  render: function() {
    var buttonClass = this.state.liked ? 'active' : '';

    return (
      <div className='photo'>
        <img src={this.props.src} />

        <div className='bar'>
          <button onClick={this.toggleLiked} className={buttonClass}>
            ♥
          </button>
          <span>{this.props.caption}</span>
        </div>
      </div>
    );
  }
});

Concepts:

          Events:
               - attached as properties of components and can trigger methods

Virtual DOM:
     - JS tree of react element and component
     - react renders virtual DOM to browser to make User Interfaces
     - observe VDOM for changes & automatically changes browser DOM to match w/ VDOM

HOW does VDOM work  :
     - Imagine you had an object that you modeled around a person
     - has every property a person can have and mirrors the person current state  ( what React does to DOM)
     - make changes to object ( add handlebar mustache, huge biceps, and Donald Trump’s hair)
      1) React runs algorithm that identifies what changed and
     2) does reconciliation( updates DOM w/ result of difference - only changes faces and arms

What happens when component is rendered to browser DOM
- component button is clicked
- State is changed
- react renders component to virtual DOM
- new virtual DOM is compared w/ previous virtual DOM
-react finds out what has changed and updates the browser DOM

Pros:
-React is like jQuery, but better, client and the server code are the same
- component makes reusing code, testing, and separating concern easier.
- can use w/ node.js, angular.js, rails, android, desktop, mobile, IOS
-fast & SCALABLE!!!
-automatically manages all Userface Interface updates when data changes
- easy debugging
     - react chrome extension - inspect DOM and find out which component is rendering a particular UI

When React is awesome:
- social network w/ notification that updates automatically in real time
- chat app => automatically updates when you get new chat message w/out refreshing page
-stock app => prices update in real time ( Mr. Friedman)

cons:
- shouldn’t mix w/ jQuery,
- verbose
- not full framework (no router nor model)

— — — — — —  DEMO — — — — — —

 <!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8" />
    <title>Awesome Presentation</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/react.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/JSXTransformer.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
</head>
<body>

</body>
</html>

This Demo is based on https://www.youtube.com/watch?v=4ZAEBxGipoA

 <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/react.js"></script>
     - react library

<script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/JSXTransformer.js"></script>
     - translate html into javascript so webpage can read it
     -easier to understand than plain javascript

<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
     -jquery

file:///Users/KhanhnhatN/wdi/presentation/react/index.html

2.

Component***
- core building block
- is just a React Class!

Inside body tag
    <div id="content"></div>  // empty div. this is where you want to display the component

    <script type="text/jsx">  //jsx syntax (convert to regular javascript)
    // javascript script tag

        var QueenKsComponent = React.createClass({ // create a component you can reference it
            render: function() {
                return (
                        <h2>My name is QueenK</h2>
                );
            }
        });

        React.render(<QueenKsComponent />, document.getElementById('content'));
     // 2 parameter ( what component you want to use, where you want to display it
    </script>

- need to make new Class when you make a component   => React.createClass( { } );

    - add functions and attributes inside the function
- Always need to have render function that return some html

    - display the html  i.e.. return ( <h2>My name is QueenK</h2>)
- React.render = 2 arguments. React.render ( What component to use ,  where you want to display)  i.e. <div id= “content”>
- Note that native HTML element names start with a lowercase letter, while custom React class names begin with an uppercase letter.
- NEW VERSION (UPDATED) ReactDOM.render() instantiates the root component, starts the framework, and injects the markup into a raw DOM element, provided as the second argument.
- ReactDOM.render should only be called after the composite components have been defined.
- render( ) returns a tree of React components that will eventually render to HTML.

Multiple Component & Properties
-Display component multiple times ( wrap it in div)
- Why? => because react can only render ONE thing
- Must put it in a div (child elements)  .

         React.render(
            <div>
                <QueenKsComponent />
                <QueenKsComponent />
                <QueenKsComponent />
                <QueenKsComponent />
            </div>,  document.getElementById('content')
        );

Property = > custom attributes (when you want additional info)

- use curly braces
- property accessed through { this.props.<name of prop> }

 <script type="text/jsx">  //jsx syntax (convert to regular javascript)
        // javascript script tag

            var QueenKsComponent = React.createClass({ // create a component you can reference it
                render: function() {
                    return (
                            <h2>{this.props.user} loves to eat {this.props.food}</h2>
                    );
                }
            });

            React.render(
                <div>
                    <QueenKsComponent user="Billyonce" food="Spaghetti Bolangese" />
                    <QueenKsComponent user="Rooster" food="American Chop Suey"/>
                    <QueenKsComponent user="Palm Sugar" food="Ceral"/>
                    <QueenKsComponent user="SeaTuna" food="Noodle soup"/>
                    <QueenKsComponent user="Ms.Yao" food="Dry Hot Pot"/>
                </div>,  document.getElementById('content')
            );
         // 2 parameter ( what component you want to use, where you want to display it
        </script>

- Children

    - Children attribute is Inside a starting and ending tag

        - e.g. <QueenKsComponent user="Jeff”></QueenKsComponent>

            var QueenKsComponent = React.createClass({ // create a component you can reference it
                render: function() {
                    return (
                            <div>
                                <h2>{this.props.user}</h2>
                                <p>{this.props.children}</p>
                            </div>
                    );
                }
            });

            React.render(
                <div>
                    <QueenKsComponent user="Jeff">He loves Baracuda</QueenKsComponent>
                    <QueenKsComponent user="Quake Head">She should have been named "Goose"</QueenKsComponent>
                </div>,  document.getElementById('content')
            );

- Events  ( Yay!!! Now user can interact w/ cool components!!)

    - something your component can do
    - camelCase naming convention.
    - <camelCaseName>: function( ) { }
    - separate the other function w/ a comma

 var QueenKsComponent = React.createClass({
            eventFunction: function(){
                alert("Ahhh Baracuda. Someone told me that " + this.props.children);
            },
            render: function() {
                return (
                        <div>
                            <h2>{this.props.user}</h2>
                            <a onClick={this.eventFunction} href="#" >Click Me</a>
                        </div>
                );
            }
        });

        React.render(
            <div>
                <QueenKsComponent user="Jeff">He loves Baracuda</QueenKsComponent>
                <QueenKsComponent user="Quake Head">She should have been named "Goose"</QueenKsComponent>
            </div>,  document.getElementById('content')
        );
