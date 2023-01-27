# react-context-api

Controla o context-api do react. Funciona para React Native.

## Installation

```sh
npm install react-context-api
```

## Usage

```js
import ContextAPI, { combineReducers } from 'react-context-api';
import { Store } from './interfaces';
import { systemProvider } from './stores/system';

const reducers = combineReducers({
    system: systemProvider
});
export const contextApi = new ContextAPI(reducers);

/**
 * Como Criar um uso de contexto com ContextAPI
 */
const useContextApi = (): Store => contextApi.useContext();
/**
 * Como criar um Provider ou Consumer que englobe toda a aplicação
 */
const Provider = contextApi.Provider;
const Consumer = contextApi.Consumer;

export { Provider, Consumer, useContextApi };
```

### Store

```js
import ContextAPI, { ActionProvider } from 'react-context-api';

const systemStore = {
    loading: true
};

export const systemProvider = (state = systemStore, action?: ActionProvider|ActionProvider[]) => {
    return ContextAPI.providerResult(state, action);
};
export default systemStore;

```

### Interface

```js
import systemStore from './stores/system';
export interface DispatchParams {
    field: string;
    reducer: string;
    payload: any;
}
export interface Store {
    dispatch: (data: DispatchParams) => void;
    store: {
        system: typeof systemStore;
    };
}
export interface ContextDispatchAction<T> {
    reducer: T;
    field: string;
    payload: any;
}
export type StoresKeys = 'system';

```

### Provider

```js
function App(): JSX.Element {
    return (
        <NavigationContainer ref={navigationRef}>
            <Provider value={contextApi.providerValues}>
                {/*YOUR COMPONENT HERE*/}
            </Provider>
        </NavigationContainer>
    );
}
export default App;

```

## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT
