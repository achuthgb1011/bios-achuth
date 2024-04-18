int k = 3;

void setup() {
  Serial.begin(9600);
}

void loop() {
  if (Serial.available()) {
    
    String x = Serial.readStringUntil('\n');
    char z[x.length()];

    
    for (int i = 0; i < x.length(); i++) {
      char p = x[i];
      char decoded;

      
      
        if (p>='A' && p<='Z') {
          decoded = p - k;
          
          if (decoded < 'A')
            decoded += 26;
          else if(decoded > 'Z')
          decoded -= 26;
          
        }
        
        else if (p>='a' && p<='z') {
          decoded = p - k;
          
          if (decoded < 'a' ) 
            decoded += 26;
          else if(decoded > 'z')
          decoded -= 26;
        }
      
      
        else
          decoded = p;
          z[i] = decoded;
      
    }
    int m = x.length();
   for (int l = 0;l<=m-1;l++)
    Serial.print(z[l]);
    Serial.print('\n');
  }
  
}
