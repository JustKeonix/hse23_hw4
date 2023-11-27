# hse23_hw4

В первой части работы мы проводим картирование чтений 6 семплов (3 перепрограммированных и 3 контрольных) для выявления экспрессии генов в разных семплах. Во второй чати мы используем найденные данные чтобы найти гены сильно изменившие свою экспрессию после перепрограммирования.

На входе у нас имеются чтения после RNA секвенирования. 3 контрольных и 3 после перепрограммирования

Проверим качество исходных чтений:
![image](https://github.com/JustKeonix/hse23_hw4/assets/24775932/e39bbdf1-44b9-43b9-9f20-9f4d0374e545)
Как видно из отчёта multiqc, качество чтений очень хорошее для всех образцов (их графики сливаются в один из-за близости и кажется что отображён только один)

Далее картируем чтения на геном мыши и посчитаем сколько чтений поподает в какие гены с помощью HTSeq
Весь код приведён в файле bio.ipynb

Результат первой части в файле ALL.counts 

|  | id | condition | reads total | mapped reads | mapped reads % | unique mapped reads | feature mapped reads |
| --- | --- | --- | --- | --- | --- | --- | --- |
| c1 | SRR3414635 | control | 20956475 | 20714433 | 98.85% | 18637060 | 17230381 |
| c2 | SRR3414636 | control | 20307147 | 20073598 | 98.85% | 18032681 | 16685471 |
| c3 | SRR3414637 | control | 20385570 | 20148671 | 98.84% | 18043401 | 16631913 |
| r1 | SRR3414629 | reprogramming | 21106089 | 20864973 | 98.86% | 18573569 | 16953209 |
| r2 | SRR3414630 | reprogramming | 15244711 | 15076441 | 98.90% | 13320521 | 12068758 |
| r3 | SRR3414631 | reprogramming | 24244069 | 23964378 | 98.85% | 21159611 | 19441257 |

Бонусная часть дз выполнялась в Google Collab (настроить окружение R локально так и не вышло до дедлайна)
https://colab.research.google.com/drive/1sHbdpdC4FuGOGxptuFlZdxUNg__OwsU5?usp=sharing
По большей части код остался почти таким же как в примере. Изменил лишь чтение данных из файлов и расчёт дифференциальной экспрессии.

Построим MA-plot чтобы изучить изменилась ли экспрессия генов между контрольными и перепрограмированными образцами
![image](https://github.com/JustKeonix/hse23_hw4/assets/24775932/df2bdb66-f488-46cd-90b4-2e730aeb7b50)

Из графика видно что много генов изменили свою экспрессию значительно и в основном в сторону увеличения (экспрессия выше по сравнению с контрольными образцами)

Построи heatmap расстояния между сэмплами
![image](https://github.com/JustKeonix/hse23_hw4/assets/24775932/ef95417c-6586-4054-abed-0ce2080e1e2c)
Как видно из графика, семплы из одной группы очень похожи, что говорит о корректности проведённого эксперимента

Построим графики дифференциальной экспрессии для 2 генов экспрессия которых изменилась больше всего (ENSMUSG00000058354.7 и ENSMUSG00000040728.15)
![image](https://github.com/JustKeonix/hse23_hw4/assets/24775932/fc1d5fa5-7875-40e7-bbeb-daef9871ce85)
