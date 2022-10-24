# @buuhvprojects/react-native-context-api

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

## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT
