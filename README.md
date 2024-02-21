<!DOCTYPE html>
<html>
<head>
	<title>Calculadora</title>
</head>
<body>

<h2>Calculadora PHP</h2>

<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
  Primer número: <input type="text" name="num1"><br>
  Segundo número: <input type="text" name="num2"><br>
  Operación:
  <select name="operacion">
     <option value="sumar">Sumar</option>
     <option value="restar">Restar</option>
     <option value="multiplicar">Multiplicar</option>
     <option value="dividir">Dividir</option>
  </select><br>
  <input type="submit" name="submit" value="Calcular">
</form>
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
	$num1 = $_POST["num1"];
	$num2 = $_POST["num2"];
	$operacion = $_POST["operacion"];

	switch($operacion) {
        case "sumar":
	        $resultado = $num1 + $num2;
	        break;
		case "restar":
	        $resultado = $num1 - $num2;
	        break;
		case "multiplicar":
			$resultado = $num1 * $num2;
			break;
		case "dividir":
			if ($num2 != 0) {
				$resultado = $num1 / $num2;
			} else {
				$resultado = "Error: división por cero";
			}
			break;
		default:
			$resultado = "Operación no válida";
	}

	echo "<br>Resultado: $resultado";
}
?>

</body>
</html>
