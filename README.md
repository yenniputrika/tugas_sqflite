mport 'package:flutter/material.dart';

void main() => runApp(App());

class App extends StatelessWidget {
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'yenni putrika / 6SIA10,
      home: Scaffold( backgroundColor: Colors.yellowGrey,
        appBar: AppBar( 
          title: Text('Input Favorite Music'),
        ),
        body: Musik(),
      ),
    );
  }
}

class DataMusik {
  String judul;
  String penyanyi;
  String tanggalrilis;

  DataMusik({this.judul, this.penyanyi, this. tanggalrilis});
}

// class Musik
class Musik extends StatefulWidget {
  _MyappState createState() => _MyappState();
}

class _MyappState extends State<Musik> {
  //deklarasi variabel
  final txtjudul = TextEditingController();
  final txtpenyanyi = TextEditingController();
  final txttanggalrilis = TextEditingController();

  List<Widget> data = [];

  onSimpan() {
    setState(() {
      data.add(ListTile(
        leading: Icon(Icons.audiotrack),
        title: Text(txtjudul.text),
        subtitle: Text(txtpenyanyi.text),
        trailing: Text(txttanggalrilis.text),
      ));
      txtjudul.clear();
      txtpenyanyi.clear();
      txttanggalrilis.clear();
    });
  }

  Widget build(BuildContext context) {
    return ListView(
      children: <Widget>[
        new Container(
          padding: EdgeInsets.all(10.0),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: <Widget>[
              TextField(
                controller: txtjudul,
                decoration: InputDecoration(hintText: 'Judul Lagu'),
              ),
              TextField(
                controller: txtpenyanyi,
                decoration: InputDecoration(hintText: 'Nama Penyanyi'),
              ),
              TextField(
                controller: txttanggalrilis,
                decoration: InputDecoration(hintText: 'Tahun Dirilis'),
              ),
              Divider(height: 5.0),
              ElevatedButton(child: Text("Simpan"), onPressed: onSimpan),
            ],
          ),
        ),
        new Column(
          children: data,
        )
      ],
    );
  }
}
