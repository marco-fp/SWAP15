

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

 * Nginx - Round Robin
</style><table class="tableizer-table">
<th></th><th>Test 1</th><th>Test 2</th><th>Test 3</th><th>Test 4</th><th>Test 5</th><th>Test 6</th><th>Test 7</th><th>Test 8</th><th>Test 9</th><th>Test 10</th><th>MEDIA</th><th>VARIANZA</th></tr>
 <tr><td>TTFT:</td><td>137,179</td><td>139,243</td><td>165,013</td><td>148,306</td><td>246,813</td><td>136,053</td><td>136,053</td><td>136,361</td><td>137,11</td><td>309,156</td><td>169,1287</td><td>59,9016607098</td></tr>
 <tr><td>FR:</td><td>100</td><td>117</td><td>92</td><td>102</td><td>97</td><td>113</td><td>104</td><td>90</td><td>101</td><td>93</td><td>100,9</td><td>8,7743312502</td></tr>
 <tr><td>RxS:</td><td>7,29</td><td>7,18</td><td>6,06</td><td>6,74</td><td>4,05</td><td>7,35</td><td>7,25</td><td>7,33</td><td>7,29</td><td>3,23</td><td>6,377</td><td>1,5084874691</td></tr>
</table>

 * Haproxy - Round Robin
<table class="tableizer-table">
<tr class="tableizer-firstrow"><th></th><th>Test 1</th><th>Test 2</th><th>Test 3</th><th>Test 4</th><th>Test 5</th><th>Test 6</th><th>Test 7</th><th>Test 8</th><th>Test 9</th><th>Test 10</th><th>MEDIA</th><th>VARIANZA</th></tr>
 <tr><td>TTFT:</td><td>142,201</td><td>150,871</td><td>186,963</td><td>133,486</td><td>133,902</td><td>135,423</td><td>137,76</td><td>134,45</td><td>134,773</td><td>135,763</td><td>142,5592</td><td>16,481342622</td></tr>
 <tr><td>FR:</td><td>105</td><td>97</td><td>116</td><td>111</td><td>99</td><td>96</td><td>127</td><td>117</td><td>116</td><td>111</td><td>109,5</td><td>10,1132476375</td></tr>
 <tr><td>RxS:</td><td>7,03</td><td>6,63</td><td>5,35</td><td>7,49</td><td>7,47</td><td>7,38</td><td>7,26</td><td>7,44</td><td>7,42</td><td>7,37</td><td>7,084</td><td>0,6641318477</td></tr>
</table>

* Siege:
 * Servidor Individual
<table class="tableizer-table">
<tr class="tableizer-firstrow"><th></th><th>Test 1</th><th>Test 2</th><th>Test 3</th><th>Test 4</th><th>Test 5</th><th>Test 6</th><th>Test 7</th><th>Test 8</th><th>Test 9</th><th>Test 10</th><th>MEDIA</th><th>VARIANZA</th></tr>
 <tr><td>AV:</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>0</td></tr>
 <tr><td>E.Time:</td><td>59,8</td><td>59,53</td><td>59,37</td><td>59,62</td><td>59,13</td><td>59,32</td><td>59,58</td><td>59,06</td><td>59,75</td><td>59,69</td><td>59,485</td><td>0,2555712556</td></tr>
 <tr><td>R.Time:</td><td>3,92</td><td>3,94</td><td>3,92</td><td>3,93</td><td>3,95</td><td>3,92</td><td>3,93</td><td>3,92</td><td>3,95</td><td>3,97</td><td>3,935</td><td>0,0171593836</td></tr>
 <tr><td>T.Rate:</td><td>3,73</td><td>3,71</td><td>3,72</td><td>3,71</td><td>3,72</td><td>3,73</td><td>3,71</td><td>3,74</td><td>3,7</td><td>3,7</td><td>3,717</td><td>0,0133749351</td></tr>
</table>
 
 * Nginx - Round Robin
 <table class="tableizer-table">
<tr class="tableizer-firstrow"><th></th><th>Test 1</th><th>Test 2</th><th>Test 3</th><th>Test 4</th><th>Test 5</th><th>Test 6</th><th>Test 7</th><th>Test 8</th><th>Test 9</th><th>Test 10</th><th>MEDIA</th><th>VARIANZA</th></tr>
 <tr><td>AV:</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>0</td></tr>
 <tr><td>E.Time:</td><td>59,8</td><td>59,6</td><td>60</td><td>59,81</td><td>59,19</td><td>59,5</td><td>59,97</td><td>59,6</td><td>59,59</td><td>59,59</td><td>59,665</td><td>0,2396872963</td></tr>
 <tr><td>R.Time:</td><td>2,01</td><td>2,03</td><td>2,02</td><td>2,01</td><td>2,01</td><td>2,01</td><td>2,01</td><td>2,01</td><td>3,53</td><td>2,02</td><td>2,166</td><td>0,4793096888</td></tr>
 <tr><td>T.Rate:</td><td>7,31</td><td>7,25</td><td>7,32</td><td>7,34</td><td>7,3</td><td>7,26</td><td>7,32</td><td>7,33</td><td>4,08</td><td>7,3</td><td>6,981</td><td>1,0197107433</td></tr>
</table>

 * Haproxy - Round Robin
<table class="tableizer-table">
<tr class="tableizer-firstrow"><th></th><th>Test 1</th><th>Test 2</th><th>Test 3</th><th>Test 4</th><th>Test 5</th><th>Test 6</th><th>Test 7</th><th>Test 8</th><th>Test 9</th><th>Test 10</th><th>MEDIA</th><th>VARIANZA</th></tr>
 <tr><td>AV:</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>100</td><td>0</td></tr>
 <tr><td>E.Time:</td><td>59,55</td><td>59,57</td><td>59,8</td><td>59,86</td><td>59,1</td><td>59,3</td><td>59,28</td><td>59,11</td><td>59,02</td><td>59,47</td><td>59,406</td><td>0,2925823721</td></tr>
 <tr><td>R.Time:</td><td>2,05</td><td>2,04</td><td>2,83</td><td>2,05</td><td>2,7</td><td>2,01</td><td>2,01</td><td>2,68</td><td>2,01</td><td>3,46</td><td>2,384</td><td>0,5061005609</td></tr>
 <tr><td>T.Rate:</td><td>7,19</td><td>7,2</td><td>4,97</td><td>7,18</td><td>5,47</td><td>7,28</td><td>7,34</td><td>5,48</td><td>7,29</td><td>4,14</td><td>6,354</td><td>1,209464528</td></tr>
</table>
