<html>
<body>

<h2></h2>
<body onload="LetturaFile()">

<h2>Magazzino Prodotti</h2>
<TABLE id="t1">
<style>
    
   <style>
    body {
        font-family: Arial, sans-serif; /* Font principale Arial */
        background-color: #14665f; /* Colore di sfondo */
        color: #333; /* Colore del testo */
        margin: 0;
        padding: 20px;
    }

    h2 {
        text-align: center; /* Allineamento del titolo */
        color: #070808; /* Colore del titolo */
        margin-bottom: 20px;
    }
    
    table {
        width: 100%; /* Larghezza della tabella */
        border-collapse: collapse; /* Unisce i bordi delle celle */
        margin: 20px;
    }

    th, td {
        border: 1px solid #ddd; /* Bordi delle celle */
        padding: 12px; /* Spaziatura interna nelle celle */
        text-align: center; /* Centra il contenuto */
    }

    th {
        background-color: #2c3e50; /* Colore di sfondo delle intestazioni */
        color: #f4f4f4; /* Colore del testo delle intestazioni */
        font-weight: bold; /* Grassetto per le intestazioni */
    }

    tr:nth-child(even) {
        background-color: #f9f9f9; /* Colore per le righe pari */
    }

    tr:hover {
        background-color: #f1f1f1; /* Cambia colore al passaggio del mouse */
    }

    a:hover {
        text-decoration: underline; /* Sottolinea i link al passaggio del mouse */
    }
    
    img {
        border-radius: 8px; /* Arrotonda gli angoli dell'immagine */
        max-width: 100px; /* Limita la larghezza massima */
        height: auto; /* Mantiene le proporzioni originali */
    }
</style>
    
<script>
function LetturaFile()
{
let xhr = new XMLHttpRequest();

xhr.open("GET", "magazzino.txt",true); //si definisce l'apertura di un file di testo presente nell'host in locale
xhr.send(); // si invia la richiesta al server

 xhr.onload = function() {

const oggetto = JSON.parse(xhr.responseText); // si crea un oggetto che è un vettore  di persone

str="<tr><th> Nome </th> <th> Categoria </th> <th>PrezzoAcquisto</th> <th>Quantita</th> <th>totale</th> <th>dettaglio</th><th>Immagine</th></tr>";


let totale = 0;
for(i=0;i<oggetto.archivio.length; i++) // si genera dinamicamente una taella in cui si inseriscono tutti dati presenti nel vettore di oggetti  
{
totale  = oggetto.archivio[i].prezzo * oggetto.archivio[i].quantita;
str = str + "<tr><td>"+oggetto.archivio[i].nome
    +"</td><td>" + oggetto.archivio[i].categoria
    + "</td><td>"+ oggetto.archivio[i].prezzo
    + "</td><td>"+oggetto.archivio[i].quantita
    + "</td><td>"+oggetto.archivio[i].prezzo*oggetto.archivio[i].quantita
    + "<td><a href=" + oggetto.archivio[i].link + ">" + oggetto.archivio[i].testo_link + "</a></td>"
    + "<td><img src="+oggetto.archivio[i].img + " width='300' height='300'><td></tr>";
}
str = str + "</table>";
document.getElementById("t1").innerHTML = str;
}
document.getElementById("b1").disabled = true; // disabilitazione del pulsante 

}
</script>

</body>
</html>
