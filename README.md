 <?php
include("vt.php"); // veritabanı bağlantımızı sayfamıza ekliyoruz.

ob_start();
session_start();
require_once 'dbconnect.php';

if (!isset($_SESSION['user'])) {
    header("Location: loginbenutzer.php");
    exit;
}
$res = mysqli_query($conn, "SELECT * FROM users WHERE userId=" . $_SESSION['user']);
$userRow = mysqli_fetch_array($res);

// Kullanıcının rolünü kontrol edin
if ($userRow['role'] != 'benutzer') {
    header("Location: hata.html");
    exit;
}
?>


<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>PO FORM</title>
	
	<link href="images/style2.css" rel="stylesheet" type="text/css">
	<link rel="stylesheet" href="images/styles.css">
	
	<script type="text/javascript">

		function geri(){

			history.back()

		}

	</script>
</head>

<body>
	<img src="images/titanic_bodrum_background.jpg" id="bg" alt="">
	<?php 

$sorgu = $baglanti->query("SELECT * FROM satin_alma_formu WHERE ID =".(int)$_GET['ID']); 
//id değeri ile düzenlenecek verileri veritabanından alacak sorgu

$sonuc = $sorgu->fetch_assoc(); //sorgu çalıştırılıp veriler alınıyor

?>

<div class="container">
	   <form id="contact" action="" method="post">
		   <br><br><br><br><left><div><a href="benutzer_yonetim.php"><img src="images/my_forms.png" width="150px"></a></div></left>
		   <center><div>Willkommen - <?php echo $userRow['userName']; ?></div></center>
	<h1 class="text-center">PO FORM</h1>
	<form class="registration-form">
		<label class="col-one-half2">
			<span class="label-text">Wer ist schreiben PO</span>
			<input type="text" value="<?php echo $sonuc['gonderen']; ?>" name="gonderen" readonly="false">
		</label>
		<label class="col-one-half2">
			<span class="label-text">Abteilung</span>
			<input type="text" name="bolum" value="<?php echo $sonuc['bolum']; ?>">
		</label>
		<label class="col-one-half2">
			<span class="label-text">Lieferant / Vendor</span>
			<input type="text" name="satici_adi" value="<?php echo $sonuc['satici_adi']; ?>">
		</label>
		<label class="col-one-half2">
			<span class="label-text">Datum</span>
			<input type="date" name="tarih" value="<?php echo $sonuc['tarih']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">1-Bezeichnung</span>
			<input type="text" name="urunaciklamabir" value="<?php echo $sonuc['urunaciklamabir']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Artikel-Nr</span>
			<input type="text" name="urunnobir" value="<?php echo $sonuc['urunnobir']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Menge</span>
			<input type="text" name="urunadetbir" value="<?php echo $sonuc['urunadetbir']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Preis (EUR)</span>
			<input type="text" name="urunfiyatbir" value="<?php echo $sonuc['urunfiyatbir']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Gesamt (EUR)</span>
			<input type="text" name="uruntopfiyatbir" value="<?php echo $sonuc['uruntopfiyatbir']; ?>">
			</label>
		<label class="col-one-half">
			<span class="label-text">2-Bezeichnung</span>
			<input type="text" name="urunaciklamaiki" value="<?php echo $sonuc['urunaciklamaiki']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Artikel-Nr</span>
			<input type="text" name="urunnoiki" value="<?php echo $sonuc['urunnoiki']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Menge</span>
			<input type="text" name="urunadetiki" value="<?php echo $sonuc['urunadetiki']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Preis (EUR)</span>
			<input type="text" name="urunfiyatiki" value="<?php echo $sonuc['urunfiyatiki']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Gesamt (EUR)</span>
			<input type="text" name="uruntopfiyatiki" value="<?php echo $sonuc['uruntopfiyatiki']; ?>">
			</label>
		
		<label class="col-one-half">
			<span class="label-text">3-Bezeichnung</span>
			<input type="text" name="urunaciklamauc" value="<?php echo $sonuc['urunaciklamauc']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Artikel-Nr</span>
			<input type="text" name="urunnouc" value="<?php echo $sonuc['urunnouc']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Menge</span>
			<input type="text" name="urunadetuc" value="<?php echo $sonuc['urunadetuc']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Preis (EUR)</span>
			<input type="text" name="urunfiyatuc" value="<?php echo $sonuc['urunfiyatuc']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Gesamt (EUR)</span>
			<input type="text" name="uruntopfiyatuc" value="<?php echo $sonuc['uruntopfiyatuc']; ?>">
			</label>
		
		<label class="col-one-half">
			<span class="label-text">4-Bezeichnung</span>
			<input type="text" name="urunaciklamadort" value="<?php echo $sonuc['urunaciklamadort']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Artikel-Nr</span>
			<input type="text" name="urunnodort" value="<?php echo $sonuc['urunnodort']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Menge</span>
			<input type="text" name="urunadetdort" value="<?php echo $sonuc['urunadetdort']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Preis (EUR)</span>
			<input type="text" name="urunfiyatdort" value="<?php echo $sonuc['urunfiyatdort']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Gesamt (EUR)</span>
			<input type="text" name="uruntopfiyatdort" value="<?php echo $sonuc['uruntopfiyatdort']; ?>">
			</label>
		
		<label class="col-one-half">
			<span class="label-text">5-Bezeichnung</span>
			<input type="text" name="urunaciklamabes" value="<?php echo $sonuc['urunaciklamabes']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Artikel-Nr</span>
			<input type="text" name="urunnobes" value="<?php echo $sonuc['urunnobes']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Menge</span>
			<input type="text" name="urunadetbes" value="<?php echo $sonuc['urunadetbes']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Preis (EUR)</span>
			<input type="text" name="urunfiyatbes" value="<?php echo $sonuc['urunfiyatbes']; ?>">
		</label>
		<label class="col-one-half">
			<span class="label-text">Gesamt (EUR)</span>
			<input type="text" name="uruntopfiyatbes" value="<?php echo $sonuc['uruntopfiyatbes']; ?>">
			</label>
		<label class="col-one-half">
			<span class="label-text"></span>
			<input type="text" name="">
			</label>
		<label class="col-one-half">
			<span class="label-text"></span>
			<input type="text" name="">
			</label>
		<label class="col-one-half">
			<span class="label-text"></span>
			<input type="text" name="">
			</label>
		<label class="col-one-half">
			<span class="label-text"></span>
			<input type="text" name="">
			</label>
		<label class="col-one-half">
			<span class="label-text">Summe Gesamt (EUR)</span>
			<input type="text" name="summetop" value="<?php echo $sonuc['summetop']; ?>">
			</label>
		<label class="col-one-half2">
		<span class="label-text">Verwendungsweg</span>
			<input type="text" name="genelaciklama" value="<?php echo $sonuc['genelaciklama']; ?>">
			</label>
		<label class="col-one-half2">
		<span class="label-text">Versandkosten?</span>
			<input type="text" name="genelaciklamaiki" value="<?php echo $sonuc['genelaciklamaiki']; ?>">
			</label>
		<label>
			<span class="label-text">Welche Hotel</span>
		<select type="text" name="hangihotel">
			<option value=""><?php echo $sonuc['hangihotel']; ?></option>
         <option value="Titanic Chaussee">Titanic Chaussee</option>
         <option value="Titanic Gendarmenmarkt">Titanic Gendarmenmarkt</option>
         <option value="Titanic Confort Mitte">Titanic Confort Mitte</option>
	 <option value="Titanic Confort Kudamm">Titanic Confort Kudamm</option>
			</select></label>
		<label>
		<span class="label-text">Welche GM</span>
<select type="text" name="hangimudur">
	<option value=""><?php echo $sonuc['hangimudur']; ?></option>
  <option value="mudur1">Yavuz Yetgin</option>
  <option value="mudur2">Yüksel Gürhan</option>
  <option value="mudur3">Mareike Görtz</option>
			</select></label>
		<label class="col-one-half3">
			<span class="label-text">GM ONAY</span>
			<input type="text" style="color: green" name="onaylamudur" value="<?php echo $sonuc['onaylamudur']; ?>" readonly="false">
			</label>
		<label class="col-one-half3">
			<span class="label-text">GM REDDET</span>
			<input type="text" style="color: red" name="reddetmudur" value="<?php echo $sonuc['reddetmudur']; ?>" readonly="false">
			</label>
		<label class="col-one-half3">
			<span class="label-text">EINKAUF ONAY</span>
			<input type="text" name="onaylaeinkauf" value="<?php echo $sonuc['onaylaeinkauf']; ?>" readonly="false">
			</label>
		<label class="col-one-half3">
			<span class="label-text">EINKAUF REDDET</span>
			<input type="text" style="color: red" name="reddeteinkauf" value="<?php echo $sonuc['reddeteinkauf']; ?>" readonly="false">
			</label>
		<label class="col-one-half3">
			<span class="label-text">PATRON ONAY</span>
			<input type="text" style="color: green" name="onaylapatron" value="<?php echo $sonuc['onaylapatron']; ?>" readonly="false">
			</label>
		<label class="col-one-half3">
			<span class="label-text">PATRON REDDET</span>
			<input type="text" style="color: red" value="<?php echo $sonuc['reddetpatron']; ?>" name="reddetpatron" readonly="false">
			</label>

		
		<br><br>
		<tr>
            
           <br><br> <td></td><td><center><button name="submit" type="submit" id="contact-submit" data-submit="...Sending">KAYDET</button></center></td>
        </tr><br><br>
		<tr>
            
            <td></td><td><center><a href="benutzer_yonetim.php"></a><button onClick="geri()">Iptal</button></center></td>
        </tr>
		<br><br>
		<div class="text-center">
		<button><a href="logoutbenutzer.php?logout">Logout</button>
		</div>
	</form>
</div>
<?php 

if ($_POST) { // Post olup olmadığını kontrol ediyoruz.
    
$ID = $_POST['ID'];
$gonderen = $_POST['gonderen'];
$bolum = $_POST['bolum'];
$satici_adi = $_POST['satici_adi'];
$tarih = $_POST['tarih'];
$urunaciklamabir = $_POST['urunaciklamabir'];
$urunnobir = $_POST['urunnobir'];
$urunadetbir = $_POST['urunadetbir'];
$urunfiyatbir = $_POST['urunfiyatbir'];
$uruntopfiyatbir = $_POST['uruntopfiyatbir'];
$urunaciklamaiki = $_POST['urunaciklamaiki'];
$urunnoiki = $_POST['urunnoiki'];
$urunadetiki = $_POST['urunadetiki'];
$urunfiyatiki = $_POST['urunfiyatiki'];
$uruntopfiyatiki = $_POST['uruntopfiyatiki'];
$urunaciklamauc = $_POST['urunaciklamauc'];
$urunnouc = $_POST['urunnouc'];
$urunadetuc = $_POST['urunadetuc'];
$urunfiyatuc = $_POST['urunfiyatuc'];
$uruntopfiyatuc = $_POST['uruntopfiyatuc'];
$urunaciklamadort = $_POST['urunaciklamadort'];
$urunnodort = $_POST['urunnodort'];
$urunadetdort = $_POST['urunadetdort'];
$urunfiyatdort = $_POST['urunfiyatdort'];
$uruntopfiyatdort = $_POST['uruntopfiyatdort'];
$urunaciklamabes = $_POST['urunaciklamabes'];
$urunnobes = $_POST['urunnobes'];
$urunadetbes = $_POST['urunadetbes'];
$urunfiyatbes = $_POST['urunfiyatbes'];
$uruntopfiyatbes = $_POST['uruntopfiyatbes'];
$genelaciklama = $_POST['genelaciklama'];
$genelaciklamaiki = $_POST['genelaciklamaiki'];
$hangihotel = $_POST['hangihotel'];
$hangimudur = $_POST['hangimudur'];
$onaylamudur = $_POST['onaylamudur'];
$reddetmudur = $_POST['reddetmudur'];
$onaylaeinkauf = $_POST['onaylaeinkauf'];
$reddeteinkauf = $_POST['reddeteinkauf'];
$onaylapatron = $_POST['onaylapatron'];
$reddetpatron = $_POST['reddetpatron'];
                               

    if ($ID<>"ID" && $gonderen<>"gonderen" && $bolum<>"bolum" && $satici_adi<>"satici_adi" && $tarih<>"tarih" && $urunaciklamabir<>"urunaciklamabir" && $urunnobir<>"urunnobir" && $urunadetbir<>"urunadetbir" && $urunfiyatbir<>"urunfiyatbir" && $uruntopfiyatbir<>"uruntopfiyatbir" && $urunaciklamaiki<>"urunaciklamaiki" && $urunnoiki<>"urunnoiki" && $urunadetiki<>"urunadetiki" && $urunfiyatiki<>"urunfiyatiki" && $uruntopfiyatiki<>"uruntopfiyatiki" && $urunaciklamauc<>"urunaciklamauc" && $urunnouc<>"urunnouc" && $urunadetuc<>"urunadetuc" && $urunfiyatuc<>"urunfiyatuc" && $uruntopfiyatuc<>"uruntopfiyatuc" && $urunaciklamadort<>"urunaciklamadort" && $urunnodort<>"urunnodort" && $urunadetdort<>"urunadetdort" && $urunfiyatdort<>"urunfiyatdort" && $uruntopfiyatdort<>"uruntopfiyatdort" && $urunaciklamabes<>"urunaciklamabes" && $urunnobes<>"urunnobes" && $urunadetbes<>"urunadetbes" && $urunfiyatbes<>"urunfiyatbes" && $uruntopfiyatbes<>"uruntopfiyatbes" && $genelaciklama<>"genelaciklama" && $genelaciklamaiki<>"genelaciklamaiki" && $hangihotel<>"hangihotel" && $hangimudur<>"hangimudur" && $onaylamudur<>"onaylamudur" && $reddetmudur<>"reddetmudur" && $onaylaeinkauf<>"onaylaeinkauf" && $reddeteinkauf<>"reddeteinkauf" && $onaylapatron<>"onaylapatron" && $reddetpatron<>"reddetpatron") { // Veri alanlarının boş olmadığını kontrol ettiriyoruz.
        
        // Veri güncelleme sorgumuzu yazıyoruz.
        if ($baglanti->query("UPDATE satin_alma_formu SET ID = '$ID', gonderen = '$gonderen', bolum = '$bolum', satici_adi = '$satici_adi', tarih = '$tarih', urunaciklamabir = '$urunaciklamabir', urunnobir = '$urunnobir', urunadetbir = '$urunadetbir', urunfiyatbir = '$urunfiyatbir', uruntopfiyatbir = '$uruntopfiyatbir', urunaciklamaiki = '$urunaciklamaiki', urunnoiki = '$urunnoiki', urunadetiki = '$urunadetiki', urunfiyatiki = '$urunfiyatiki', uruntopfiyatiki = '$uruntopfiyatiki', urunaciklamauc = '$urunaciklamauc', urunnouc = '$urunnouc', urunadetuc = '$urunadetuc', urunfiyatuc = '$urunfiyatuc', uruntopfiyatuc = '$uruntopfiyatuc', urunaciklamadort = '$urunaciklamadort', urunnodort = '$urunnodort', urunadetdort = '$urunadetdort', urunfiyatdort = '$urunfiyatdort', uruntopfiyatdort = '$uruntopfiyatdort', urunaciklamabes = '$urunaciklamabes', urunnobes = '$urunnobes', urunadetbes = '$urunadetbes', urunfiyatbes = '$urunfiyatbes', uruntopfiyatbes = '$uruntopfiyatbes', genelaciklama = '$genelaciklama', genelaciklamaiki = '$genelaciklamaiki', hangihotel = '$hangihotel', hangimudur = '$hangimudur', onaylamudur = '$onaylamudur', reddetmudur = '$reddetmudur', onaylaeinkauf = '$onaylaeinkauf', reddeteinkauf = '$reddeteinkauf', onaylapatron = '$onaylapatron', reddetpatron = '$reddetpatron'  WHERE ID =".$_GET['ID'])) 
        {
            header("location:benutzer_yonetim.php"); 
            // Eğer güncelleme sorgusu çalıştıysa ekle.php sayfasına yönlendiriyoruz.
        }
        else
        {
            echo "Hata oluştu"; // id bulunamadıysa veya sorguda hata varsa hata yazdırıyoruz.
        }
    }
}
?>
</body>
</html>
