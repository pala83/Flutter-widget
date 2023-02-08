# Mercado_liniers

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.


# Arbol de widgets 
![arbol de widgets](https://miro.medium.com/max/640/1*z_A9htJmE6THrxZeloVRiw.webp)

~~~ dart
@override
Widget build(BuildContext){
    return new Scaffold(
        appBar: new AppBar(
            title: new Text(widget.title),
        ),
        body: new Center(
            child: new Column(
                mainAxiasAligment: MainAxiasAligment.center,
                children: <Widget>[
                    new Text(
                        'You have pushed the button this many times:',
                    ),
                    new Text(
                        '$_center',
                        style: Theme.of(context).textTheme.display1,
                    ),
                ],
            ),
        ),
        floatingActionButton: new FloatingActionButton(
            onPressed: _incrementCounter,
            tooltip: 'Increment',
            child: new Icon(Icons.add),
        ),
    );
}
~~~

## Cero, uno y varios hijos

| Cero hijos | Un hijo | Varios hijos |
|------------|---------|--------------|
| Text       | Container| Column |
| Image      | Padding | Row |
| RichText   | RaisedButton | Stack |
| Icon       | Align    | Wrap |
|            | Center   | ListView |
|            | Positioned | GridView |


# Stateless Widget
Widget sin estadom es un widget que nos permite dibujar una sola vez, y no se permite cambiar los valores mostrados.

Se usa generalmente para mostrar partes de la interfaz que no deben se cambiar sus valores o al menos ellos deben controlar el estado.

~~~ dart
class Frog extends StatelessWidget {
    const Frog({
        Key key,
        this.color,
        this.child,
    }) : super(Key: key);

    final Color color;
    final Widget child;

    @override
    Widget build(BuildContext context){
        return Container(color: color, child: child);   
    }
}
~~~

# Stateful Widget
Widget con estado, es un widget que al igual que el anterior, nos permte dibujar en pantalla, pero este, a su vez, tiene metodos para poder cambiar los valores, es decir, poder mostrar cambios en pantalla, para llos solo basta con lamar ala metodo "setState", cambiar los valores que imprimen y el cambio es inmediato, debido a que se vuelve a dibujar toda la interfaz necesaria

~~~ dart
class Bird extends StatefulWidget{
    const Bird({
        Key: key,
        this.color = const Color(0xFFFFE308),
        this.child,
    }) : super(Key: key);

    final Color color;
    final Widget child;

    _BirdState createState() => _BirdState();
}

class _BirdState extends State<Bird> {
    double _size = 1.0;

    void grow(){
        setState(() { _size += 0.1; });
    }

    @override
    Widget build(BuildContext context) {
        return Container(
            color: widget.color,
            transformd: Matrix4.diagonal3Values(_size, _size, 1.0),
            child: widget.child,
        );
    }
}
~~~