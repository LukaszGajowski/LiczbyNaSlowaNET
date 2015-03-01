LiczbyNaSłowaNET
================

LiczbyNaSłowaNET to biblioteka, która umożliwia konwersje liczb na odpowiedniki słowne z zachowaniem polskiej gramatyki.

Możliwości biblioteki są następujące:

* Zamiana liczb na odpowiedniki słowne z zachowaniem polskiej gramatyki czyli  {"tysiac","tysiace","tysiecy"},
* zamiana liczb typu decimal i int,
* zamiana liczb typu decimal na odpowiedniki walutowe.

Projekt składa się z 2 solucji:

1. LiczbyNaSlowaNET - jest to głowna bliblioteka służąca do zamiany liczb na słowa.
2. LiczbyNaSlowaNET_Testy - jest to biblioteka z testami.

### Szybki start:

Biblioteka LiczbyNaSłowaNET to statyczna klasa NumberToText z metodą Convert, która przyjmuje liczbę typu int lub decimal i zwraca string z odpowiednikiem słownym danej liczby.

Przykłady zastosowań z testów dostępnych w projekcie:

* Zamiana liczb na odpowiedniki słowne (zachowana polskiej gramatyki)
 -  Assert.AreEqual("osiemdziesiat cztery", NumberToText.Convert(84));
 -  Assert.AreEqual("sto dwadziescia tysiecy trzydziesci", NumberToText.Convert(120030));
 -  Assert.AreEqual("osiemset dwadziescia cztery tysiace siedemset dwa", NumberToText.Convert(824702));
 -  Assert.AreEqual("jeden tysiac dwa", NumberToText.Convert(1002)); 

* Zamiana liczb typu decimal:
 -   Assert.AreEqual("czternascie tysiecy sto dwadziescia trzy", NumberToText.Convert(14100.23M));
 -   Assert.AreEqual("trzynascie zero", NumberToText.Convert(13.0M));

* Zamiana liczb typu decimal na odpowiedniki walutowe:
 - Assert.AreEqual("jeden zloty dwadziescia dwa grosze", NumberToText.Convert(1.22M,  NumberToText.Currency.PL));
 -   Assert.AreEqual("dwa zlote szescdziesiat osiem groszy", NumberToText.Convert(2.68M, NumberToText.Currency.PL));
 -   Assert.AreEqual("zero zlotych dwanascie groszy", NumberToText.Convert(0.12M, NumberToText.Currency.PL));
 
* Można również przesłać własny string, który rozdzieli liczby po przecinku.

 var options = new NumberToTextOptions
            {
                curency = Currency.PL,
                SplitDecimal = "i"
            };

Assert.AreEqual("dwanascie zlotych i dwadziescia trzy grosze", NumberToText.Convert(12.23M, options));
            

Biblioteka jest bezpieczna w środowisku wielowątkowym(ThreadSafety)

Biblioteka jest implementacją algorytmu bazującego na prawidłowości, że każda liczba składa się z trzy cyfrowych elementów oddzielonych rzędami wielkości.

Szczegóły tutaj: http://www.algorytm.org/inne/zamiana-liczby-na-slowa-z-polska-gramatyka.html

