

## Práctica 4 - Servidores Web de Altas Prestaciones (2015)
### *Marco Manuel Fernández Pranno*

**Sentencias de ejecución de Benchmarks y configuración de balanceadores:**

Las órdenes, respectivamente, utilizadas en Apache Benchmark y en Siege para la toma de medidas de rendimiento son:

`ab -n 1000 -c 5 http://<Ip_Objetivo>/carga.php`

`siege -b -t60S -v http://<Ip_Objetivo>/carga.php`

En cada caso de han tomado 10 medidas de las variables propuestas en el guión de prácticas, siendo éstas en Apache Benchmark:
* Time taken from tests
* Failed requests
* Requests per second

Y por otro lado, en Siege:

* Availability
* Elapsed time
* Response time
* Transaction rate

Con ambas aplicaciones he realizado 3 baterías de pruebas, una en el servidor individual, una en la granja web balanceada con Nginx y la última en la granja web balanceada con Haproxy.

Las tablas de datos recogidos son las siguientes:

* Apache Benchmark:
 * Servidor Individual
</style><table class="tableizer-table">
<th></th><th>Test 1</th><th>Test 2</th><th>Test 3</th><th>Test 4</th><th>Test 5</th><th>Test 6</th><th>Test 7</th><th>Test 8</th><th>Test 9</th><th>Test 10</th><th>MEDIA</th><th>VARIANZA</th></tr>
 <tr><td>TTFT:</td><td>263,39</td><td>262,389</td><td>265,72</td><td>266,675</td><td>263,045</td><td>263,938</td><td>265,421</td><td>266,539</td><td>265,667</td><td>265,683</td><td>264,8467</td><td>1,5240824599</td></tr>
 <tr><td>FR:</td><td>108</td><td>101</td><td>73</td><td>92</td><td>102</td><td>91</td><td>106</td><td>112</td><td>99</td><td>97</td><td>98,1</td><td>11,0398268908</td></tr>
 <tr><td>RxS:</td><td>3,8</td><td>3,81</td><td>3,76</td><td>3,75</td><td>3,8</td><td>3,79</td><td>3,77</td><td>3,75</td><td>3,76</td><td>3,76</td><td>3,775</td><td>0,0227303028</td></tr>
</table>
