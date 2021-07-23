# Hi :vulcan_salute:

Hello, my name is Alef and I am a student in the 7th period of the Computer Science course at the Federal University of Itajubá.
I am currently focusing my efforts on mastering Front-end technologies, but I never forget the Back-end. :computer:

---
## My Skills

<img align="center" alt="js" height="70" widht="80" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg"
  style="max-widht:100%"> 
</img> 
<img align="center" alt="HTML5" height="70" widht="80" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg"
  style="max-widht:100%"> 
</img>
<img align="center" alt="CSS3" height="70" widht="80" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original.svg"
  style="max-widht:100%"> 
</img>
<img align="center" alt="react" height="70" widht="80" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg"
  style="max-widht:100%"> 
</img>
<img align="center" alt="Bootstrap" height="70" widht="80" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/bootstrap/bootstrap-plain-wordmark.svg"
  style="max-widht:100%"> 
</img>
<img align="center" alt="C" height="70" widht="80" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg"
  style="max-widht:100%"> 
</img>
<img align="center" alt="Java" height="70" widht="80" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg"
  style="max-widht:100%"> 
</img>
<img align="center" alt="Electron" height="70" widht="80" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/electron/electron-original.svg"
  style="max-widht:100%"> 
</img>





---
## Connect with me:

<a href="https://www.linkedin.com/in/alef-paula-aa98041ba/" target="_blank">
  <img align="center" alt="alef-linkedin" height="30" widht="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linkedin/linkedin-original.svg"
  style="max-widht:100%">                      
</a>

---
[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=Tuturado&layout=compact)](https://github.com/Tuturado/github-readme-stats)


<!DOCTYPE html>
<html>
<head>
	<meta charset=utf-8 />
	<title>Contador de Visitas</title>

</head>
<body>

<?php

	function get_num_visitas(){
		//conectar
		$link = mysql_connect('localhost', 'root', '');
		if (!$link) {
			die('Não foi possível conectar: ' . mysql_error());
		}
		
		mysql_select_db("contador");
		$query = "SELECT total " .
				 "FROM `visitas` " .
				 "ORDER BY total ASC LIMIT 1";
		$result = mysql_query($query);
		if (!$result) {
			$message  = 'Invalid query: ' . mysql_error() . "\n";
			$message .= 'Whole query: ' . $query;
			die($message);
		}
		if (mysql_num_rows($result) == 0) {
			echo "No rows found, nothing to print so am exiting";
			exit;
		}
		$row = mysql_fetch_array($result);
		mysql_close($link);
		return $row["total"];
		//fazer consulta
		//retornar total
	}

	function imprime_visitas($contador){
		return "<h1>" . $contador . "</h1>";
	}
	
	function contar_visita(){
		//conectar
		$link = mysql_connect('localhost', 'root', '');
		if (!$link) {
			die('Não foi possível conectar: ' . mysql_error());
		}
		
		mysql_select_db("contador");
		$query = "UPDATE `visitas` " .
				 "SET total = total + 1";
		$result = mysql_query($query);
		if (!$result) {
			$message  = 'Invalid query: ' . mysql_error() . "\n";
			$message .= 'Whole query: ' . $query;
			die($message);
		}
		mysql_close($link);
	}

	contar_visita();
	$contador = get_num_visitas();
	echo imprime_visitas($contador);

?>

 
</body>
</html>
