<?php
session_start();

if ($_SESSION['degre'] < 0)
  negatif();
else 
  positif();

function	negatif()
{
  $x1 = -2.1;
  $x2 = 1.25;
  $y1 = -1.2;
  $y2 = 1.2;
  $zoom = 200;
  $iterations_max = $_SESSION['nombre'];
  
  $image_x = ($x2 - $x1) * $zoom;
  $image_y = ($y2 - $y1) * $zoom;
  
  $image = imagecreatetruecolor($image_x, $image_y);
  $blanc = imagecolorallocate($image, 255, 255, 255);
  $noir  = imagecolorallocate($image, 0, 0, 0);
  imagefill($image, 0 ,0 , $blanc);
  $couleur = array();
  for($i = 0; $i < $iterations_max; $i++)
    $couleur[$i] = imagecolorallocate($image, 0, 0, $i*255/$iterations_max);
  
  for($x = 0; $x < $image_x; $x++)
    {
      for($y = 0; $y < $image_y; $y++)
	{
	  $c_r = $x/$zoom+$x1;
	  $c_i = $y/$zoom+$y1;
	  $z_r = 0;
	  $z_i = 0;
	  $i = 0;
	  $n = $_SESSION['degre'];
	  $m = 0;
	  while($m < 2 AND $i < $iterations_max)
	    {
	      $z_r = $z_r + $c_r;
	      $z_i = $z_i + $c_i;
	      
	      $m = sqrt($z_r*$z_r + $z_i*$z_i);
	      if ($z_i >= 0)
		$arg = acos($z_r/ $m);
	      else
		$arg = acos($z_r/ $m) * (-1);
	      
	      $z_r = pow($m, $n) * cos( $n * $arg) + $c_r;
	      $z_i = pow($m, $n) * sin( $n * $arg) + $c_i;
	      $i++;
	    }
	  if($i == $iterations_max)
	    imagesetpixel($image, $x, $y, $noir);
	  else
	    imagesetpixel($image, $x, $y, $couleur[$i]);
	}
    }
  header('Content-type: image/png');
  imagepng($image);
}

function        positif()
{
  $x1 = -2.1;
  $x2 = 1.25;
  $y1 = -1.2;
  $y2 = 1.2;
  $zoom = 200;
  $iterations_max = $_SESSION['nombre'];

  $image_x = ($x2 - $x1) * $zoom;
  $image_y = ($y2 - $y1) * $zoom;

  $image = imagecreatetruecolor($image_x, $image_y);
  $blanc = imagecolorallocate($image, 255, 255, 255);
  $noir  = imagecolorallocate($image, 0, 0, 0);
  imagefill($image, 0 ,0 , $blanc);
  $couleur = array();
  for($i = 0; $i < $iterations_max; $i++)
    $couleur[$i] = imagecolorallocate($image, 0, 0, $i*255/$iterations_max);

  for($x = 0; $x < $image_x; $x++)
    {
      for($y = 0; $y < $image_y; $y++)
	{
	  $c_r = $x/$zoom+$x1;
	  $c_i = $y/$zoom+$y1;
	  $z_r = 0;
	  $z_i = 0;
	  $i = 0;
	  $n = $_SESSION['degre'];

	  do
	    {
	      $tmp = pow(($z_r * $z_r + $z_i * $z_i), ($n / 2)) * cos( $n * atan2($z_i,$z_r)) + $c_r;
	      $z_i = pow(($z_r * $z_r + $z_i * $z_i), ($n / 2)) * sin( $n * atan2($z_i,$z_r)) + $c_i;
	      $z_r = $tmp;	      $i++;
	    }
	  while($z_r*$z_r + $z_i*$z_i < 4 AND $i < $iterations_max AND $tmp != 0);
	  
	  if($i == $iterations_max)
	    imagesetpixel($image, $x, $y, $noir);
	  else
	    imagesetpixel($image, $x, $y, $couleur[$i]);
	}
    }
  header('Content-type: image/png');
  imagepng($image);
}

?>
