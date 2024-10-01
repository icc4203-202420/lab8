# Laboratorio: PokeDex

## Introducción

Este proyecto busca desarrollar una aplicación básica, con una autentificación simulada, que permita a usuarios ver los datos de un pokemón con la PokeAPI [PokéAPI](https://pokeapi.co/). Para ello, haremos uso de la navegación basada en archivos, los componentes de React Native Elements y el scroll loading de las Flat List.

## Objetivos

1. Implementar una pantalla de login falso que no valide credenciales, pero que cambie el estado de la aplicación para permitir el acceso a las rutas protegidas.
2. Implementar navegación por archivos utilizando Expo Router.
3. Utilizar React Native Elements.
4. Conectar la aplicación a la PokéAPI para permitir la búsqueda y selección de Pokémon.
5. Implementar un mecanismo de carga de pokemones, que utilice el paginamiento de la pokeapi y los eventos de scroll de la FlatList para dar la idea de un scroll infinito ((ejemplo)[https://medium.com/react-native-development/how-to-use-the-flatlist-component-react-native-basics-92c482816fe6]).

## Características a Desarrollar

Las [FlatList](https://reactnative.dev/docs/flatlist) de react native permiten saber cuando se ha llegado al final de la lista, lo que se puede utilizar para cargar más elementos, esto gracias a que FlatList hereda las propiedades de VirtualizedList, en particular, la propiedad [onReachedThreshold](https://reactnative.dev/docs/virtualizedlist#onendreachedthreshold), que nos permite gatillar un evento cuando el usuario se desliza lo suficiente.

Sabiendo esto, se debe realizar una aplicación cuya priemra vista sea un login, este al validar que los datos son correctos, debe mostrar una lista de pokemones base (ver el endpoint `https://pokeapi.co/api/v2/pokemon`), y a medida que este desliza hacia abajo, se deben cargar más pokemones, hasta que se hayan cargado todos los pokemones de la pokeapi, o que el usuario debe de deslizar hacia abajo.

La lista debe tener en la parte superior un buscador, el cual permita filtrar los pokemones que se han cargado por nombre. Cuando se hace click en un pokemón, se debe mostrar una pantalla con los detalles del pokemón seleccionado, incluyendo una FlatList horizontal con los sprites del mismo, para que el usuario pueda ver las imágenes de su pokemon sin deslizarse verticalmente.

En todo momento debe haber una navbar superior indicando el nombre del usuario con el que se ha logeado, y un botón de logout que permita volver a la pantalla de login.

## Bonus

Mantener el estado de la aplicación al recargar la página. Para ello, se puede hacer uso de la librería [SecureStore](https://docs.expo.dev/versions/latest/sdk/securestore/), que permite guardar información sensible en el dispositivo del usuario. Sin embargo, esta biblioteca no es compatible con la versión web de expo, por lo que se debe hacer uso de la librería [AsyncStorage](https://react-native-async-storage.github.io/async-storage/docs/install/), que permite guardar información en el dispositivo del usuario, pero no de forma segura. Se debe implementar de manera el código específico tanto para web como para móvile, de modo tal que se utilice un módulo u otro dependiendo de la plataforma en la que se esté ejecutando la aplicación.
