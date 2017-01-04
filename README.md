# adc-arduino-oversampling
augmenter la precision du convertisseur ADC (10 bits) de l'arduino par la methode du surechantillonnage

Definitions : Le quantum du CAN est q=Vref / 2^n  avec n = nombre bits de l'ADC (ici 10 bits pour l'arduino Yun)
exemple pour Vref = 5v ,    q= 5 / 2^10   , en python >>> 5.0 / (2**10)
q = 0.0048828125v
une autre maniere de reduire q est d'avoir Vref plus petit 
exemple pour Vref = 3.3v ,    q= 3.3 / 2^10   , en python >>> 3.3 / (2**10)
q = 0.00322265625v
Le but est de reduire q, par le biais du surechantillonnage on peut augmenter alors la precision de la mesure .

pour 16-bits de precision, n = 6, soit 4^6 = 4096 samples.  
il faut faire la somme des 4096 echantillons et la diviser par 2^6 = 64.
analogRead() max possible est alors  4096*1023/64 = 65472. 
pour Vref = 3.3v ,    q= 3.3 / 2^16  , en python >>> 3.3 / (2**16) 
q = 0.05035 mV
