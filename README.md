# react-planner [WIP]
*react-planner* is a React Component for plans design.
Draw a 2D floorplan and navigate it in 3D mode.

[![npm](https://img.shields.io/npm/v/react-planner.svg?maxAge=2592000?style=plastic)](https://www.npmjs.com/package/react-planner)
![javascript](https://img.shields.io/badge/javascript-ES6-fbde34.svg)
![react-version](https://img.shields.io/badge/react%20version-15.0.0%20or%20later-61dafb.svg)

## Features
- Fully customizable catalog
- 3D realtime view
- Pan & zoom support
- ES6 syntax

## Demo

[https://cvdlab.github.io/react-planner](https://cvdlab.github.io/react-planner)


## Usage
```
 import React from 'react';
 import ReactDOM from 'react-dom';
 import {Map} from 'immutable';
 import {createStore} from 'redux';
 import {Provider} from 'react-redux';

 import MyCatalog from './catalog/mycatalog';

 import {
   Models as PlannerModels,
   reducer as PlannerReducer,
   ReactPlanner,
   Plugins as PlannerPlugins,
 } from 'react-planner';


 //define state
 let AppState = Map({
   'react-planner': new PlannerModels.State()
 });

 //define reducer
 let reducer = (state, action) => {
   state = state || AppState;
   state = state.update('react-planner', plannerState => PlannerReducer(plannerState, action));
   return state;
 };

 let store = createStore(reducer, null, window.devToolsExtension ? window.devToolsExtension() : f => f);

 let plugins = [
   PlannerPlugins.Keyboard(),
   PlannerPlugins.Autosave('react-planner_v0'),
   PlannerPlugins.ConsoleDebugger(),
 ];

 //render
 ReactDOM.render(
   (
     <Provider store={store}>
       <ReactPlanner catalog={MyCatalog} width={width} height={height} plugins={plugins}
                     stateExtractor={state => state.get('react-planner')}
       />
     </Provider>
   ),
   document.getElementById('app')
 );

```

## Docs

Cooming soon!

## Contributing
Your contributions (issues and pull request) are very appreciated!

## Authors
- [chrvadala](https://github.com/chrvadala)
- [danilosalvati](https://github.com/danilosalvati)
- [enricomarino](https://github.com/enricomarino)
- [federicospini](https://github.com/federicospini)


Developed @ [CVDLAB](http://cvdlab.org/)

## License
MIT