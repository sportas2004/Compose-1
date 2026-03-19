package org.example.project


import androidx.compose.desktop.ui.tooling.preview.Preview
import androidx.compose.foundation.background
import androidx.compose.foundation.border
import androidx.compose.foundation.clickable
import androidx.compose.foundation.layout.*
import androidx.compose.material.Button
import androidx.compose.material.MaterialTheme
import androidx.compose.material.Text
import androidx.compose.material.TextField
import androidx.compose.runtime.*
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.unit.dp
import androidx.compose.ui.window.Window
import androidx.compose.ui.window.application




enum class Pantalla { EJ1, EJ2, EJ3, EJ4, EJ5, EJ6 }


@Composable
@Preview
fun App() {
    var pantalla by remember { mutableStateOf<Pantalla?>(null) }


    if (pantalla == null) {
        Column(modifier = Modifier.padding(16.dp)) {
            Text("Menú de Ejercicios", style = MaterialTheme.typography.h5)
            Pantalla.values().forEach {
                Button(onClick = { pantalla = it }, modifier = Modifier.padding(4.dp)) {
                    Text(it.name)
                }
            }
        }
    } else {
        Column(modifier = Modifier.padding(16.dp)) {
            Button(onClick = { pantalla = null }) { Text("Volver al menú") }
            Spacer(Modifier.height(16.dp))
            when (pantalla) {
                Pantalla.EJ1 -> Ejercicio1()
                Pantalla.EJ2 -> Ejercicio2()
                Pantalla.EJ3 -> Ejercicio3()
                Pantalla.EJ4 -> Ejercicio4()
                Pantalla.EJ5 -> Ejercicio5()
                Pantalla.EJ6 -> Ejercicio6()
                null -> {}
            }
        }
    }
}
@Composable
fun Ejercicio1() {
    var botonEjercicio1 by remember { mutableStateOf(true) }

    Button(onClick = {botonEjercicio1=!botonEjercicio1}){
        if(botonEjercicio1) Text("Pulsa el boton")
        else Text("Has pulsado el boton")
    }
}
@Composable
fun Ejercicio2() {
    var botonEjercicio2 by remember { mutableStateOf(false) }
    Column {
        Row(modifier = Modifier.padding(2.dp)) {
            if (botonEjercicio2) Text("Hola")
            else {


            }
        }
        Row(modifier = Modifier) {

                Column {
                    Button(onClick = { botonEjercicio2 = true }) { Text("Mostrar") }
                }

            Spacer(modifier = Modifier.padding(5.dp))

                Column {
                    Button(onClick = { botonEjercicio2 = false }) { Text("Ocultar") }
                }


        }
    }
}
@Composable
fun Ejercicio3() {
    var pestañaEjercicio3 by remember { mutableStateOf("Inicio") }
    when (pestañaEjercicio3) {
        "Inicio" -> {
            Inicio(
                { pestañaEjercicio3 = "Adelante" },
                { pestañaEjercicio3 = "Atras" }
            )
        }
        "Adelante" -> Adelante({ pestañaEjercicio3="Inicio"})
        "Atras" -> Atras({pestañaEjercicio3="Inicio"})
    }
}
@Composable
fun Inicio(Adelante:()-> Unit,Atras:()-> Unit){
    Text("Bienvenido")
    Button(onClick = Adelante){
        Text("Pantalla opcion 1")
    }
    Button(onClick = Atras){
        Text("Pantalla opcion 2")
    }
}
@Composable
fun Adelante(Inicio:()-> Unit){
    Text("Pantalla opcion 1")
    Button(onClick = Inicio){
        Text("Pantalla opcion 1")
    }
}
@Composable
fun Atras(Inicio:()-> Unit){
    Text("Pantalla opcion 2")
    Button(onClick = Inicio){
        Text("Pantalla opcion 2")
    }
}
@Composable
fun Ejercicio4() {
    var contador by remember { mutableStateOf(0) }


    Column {
        Column {
            Row {
                Text("$contador")
            }
        }


        Column {
            Row(modifier = Modifier.padding(2.dp)) {
                Column {
                    Button(onClick = {contador++}){
                        Text("Incrementa")
                    }
                }

                Spacer(modifier = Modifier.padding(5.dp))
                Column {
                    Button(onClick = {contador--}){
                        Text("Decrece")
                    }
                }
            }
        }
    }
}
@Composable
fun Ejercicio5() {
    var texto by remember { mutableStateOf("") }
    var botonEjercicio5 by remember { mutableStateOf(false) }


    TextField(value = texto, onValueChange = {
        botonEjercicio5 = false
        texto = it
    }, placeholder = { Text("Introduce tu nombre...") })


    Button(onClick = { botonEjercicio5 = true }) {
        Text("Saludar")
    }
    if (botonEjercicio5) {
        Text("Hola $texto")
    }
}
@Composable
fun Ejercicio6() {
    var botonEjercicio6 = remember { mutableStateListOf(false,false,false,false,false,false,false,false,false) }


    Column {
        Column {
            Row {
                Row {
                    Box(modifier = Modifier.background(Color.White).size(width = 100.dp, height = 100.dp).border(width = 3.dp, color = Color.Black).clickable{botonEjercicio6[0]=!botonEjercicio6[0]}, contentAlignment = Alignment.Center){
                        Text(if(botonEjercicio6[0]){"\u2714"}  else {""})
                    }
                }
                Row{
                    Box(modifier = Modifier.background(Color.White).size(width = 100.dp, height = 100.dp).border(width = 3.dp, color = Color.Black).clickable{botonEjercicio6[1]=!botonEjercicio6[1]}, contentAlignment = Alignment.Center){
                        Text(if(botonEjercicio6[1]){"\u2714"}  else {""})
                    }
                }
                Row {
                    Box(modifier = Modifier.background(Color.White).size(width = 100.dp, height = 100.dp).border(width = 3.dp, color = Color.Black).clickable{botonEjercicio6[2]=!botonEjercicio6[2]}, contentAlignment = Alignment.Center){
                        Text(if(botonEjercicio6[2]){"\u2714"}  else {""})
                    }
                }
            }
        }
        Column {
            Row {
                Row {
                    Box(modifier = Modifier.background(Color.White).size(width = 100.dp, height = 100.dp).border(width = 3.dp, color = Color.Black).clickable{botonEjercicio6[3]=!botonEjercicio6[3]}, contentAlignment = Alignment.Center){
                        Text(if(botonEjercicio6[3]){"\u2714"}  else {""})
                    }
                }
                Row {
                    Box(modifier = Modifier.background(Color.White).size(width = 100.dp, height = 100.dp).border(width = 3.dp, color = Color.Black).clickable{botonEjercicio6[4]=!botonEjercicio6[4]}, contentAlignment = Alignment.Center){
                        Text(if(botonEjercicio6[4]){"\u2714"}  else {""})
                    }
                }
                Row {
                    Box(modifier = Modifier.background(Color.White).size(width = 100.dp, height = 100.dp).border(width = 3.dp, color = Color.Black).clickable{botonEjercicio6[5]=!botonEjercicio6[5]}, contentAlignment = Alignment.Center){
                        Text(if(botonEjercicio6[5]){"\u2714"}  else {""})
                    }
                }
            }
        }
        Column {
            Row {
                Row {
                    Box(modifier = Modifier.background(Color.White).size(width = 100.dp, height = 100.dp).border(width = 3.dp, color = Color.Black).clickable{botonEjercicio6[6]=!botonEjercicio6[6]}, contentAlignment = Alignment.Center){
                        Text(if(botonEjercicio6[6]){"\u2714"}  else {""})
                    }
                }
                Row {
                    Box(modifier = Modifier.background(Color.White).size(width = 100.dp, height = 100.dp).border(width = 3.dp, color = Color.Black).clickable{botonEjercicio6[7]=!botonEjercicio6[7]}, contentAlignment = Alignment.Center){
                        Text(if(botonEjercicio6[7]){"\u2714"}  else {""})
                    }
                }
                Row {
                    Box(modifier = Modifier.background(Color.White).size(width = 100.dp, height = 100.dp).border(width = 3.dp, color = Color.Black).clickable{botonEjercicio6[8]=!botonEjercicio6[8]}, contentAlignment = Alignment.Center){
                        Text(if(botonEjercicio6[8]){"\u2714"}  else {""})
                    }
                }
            }
        }
    }
}
fun main() = application {
    Window(onCloseRequest = ::exitApplication, title = "Ejercicios Compose Desktop") {
        App()
    }
}
