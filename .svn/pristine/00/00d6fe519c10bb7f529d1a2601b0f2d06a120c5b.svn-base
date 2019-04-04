<html>
	<head>
		<title>Pimp My Fractale</title>
		<link rel="stylesheet" type="text/css" href="style.css">
	</head>
	<body>
   		<center>
   		<div class="text">
		<center><h3>Interface Pimp My Fractale</h3></center>
		<br>
		<form method="post" action="index.php"><center>
   			<p><h4>Nombre d itération :</h4></p>
		<p><input type="text" name="Nombre_d_itération" /></p>
   			<p><h4>Degré :</h4></p>
		<p><input type="text" name="Degre" /></p>
		<p><input type="submit" name="Valider" value="Valider"/></p>
		</div>
		</center></form>
   		</center>
	</body>
</html>

<?php
session_start();

	if (isset($_POST["Valider"]))
	{
		if (isset($_POST["Nombre_d_itération"]) AND isset($_POST["Degre"]))
		{
			$nombre = $_POST["Nombre_d_itération"];
			$degre = $_POST["Degre"];
					
			  if (is_numeric($degre))
				{
				  	$_SESSION['degre'] = $degre;
				}
			  else {
				  ?>
				  <script>alert("votre champ degre n'est pas valide");</script>
				  <script>alert("degre par default:2");</script>
       			   <?php
				$_SESSION['nombre'] = $nombre;
				$_SESSION['degre'] = 2;
			  
			  }
			if (is_numeric($nombre))
			  $_SESSION['nombre'] = $nombre;
			  else
			    {
			  ?>
			  <script>alert("votre champ nombre d'iteration n'est pas valide");</script>
			  <script>alert("iteration par default:50");</script>
			   <?php
			 $_SESSION['nombre'] = 50;
			 $_SESSION['degre'] = $degre;
			    }
		}
		?>
		<script>document.location.href= "/CMG/mat1/mat1/test.php";</script>
								      <?php
	}
?>