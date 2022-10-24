# @buuhvprojects/react-context-api

Controla o context-api do react

## Installation

```sh
npm install @buuhvprojects/react-context-api
```

## Usage

```js
import ContextAPI, { combineReducers } from '@buuhvprojects/react-context-api';
import { Store } from './interfaces';
import { systemProvider } from './stores/system';
import { themeProvider } from './stores/theme';

const reducers = combineReducers({
    system: systemProvider,
    theme: themeProvider,
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
import ContextAPI, { ActionProvider } from '@buuhvprojects/react-context-api';

const systemStore = {
    loading: true
};

export const systemProvider = (state = systemStore, action?: ActionProvider) => {
    return ContextAPI.providerResult(state, action);
};
export default systemStore;

```

## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT
