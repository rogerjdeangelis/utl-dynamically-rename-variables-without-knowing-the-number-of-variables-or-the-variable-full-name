# utl-dynamically-rename-variables-without-knowing-the-number-of-variables-or-the-variable-full-name
Dynamically rename variables without knowing the number of variables or the variable full name
    Dynamically rename variables without knowing the number of variables or the variable full name                                      
                                                                                                                                        
    You know the variable prefixes and that the variables are side by side in the pdv.                                                  
    We also neeed to append the data.                                                                                                   
                                                                                                                                        
    github                                                                                                                              
    https://tinyurl.com/y8cp7oe6                                                                                                        
    https://github.com/rogerjdeangelis/utl-dynamically-rename-variables-without-knowing-the-number-of-variables-or-the-variable-full-nam
                                                                                                                                        
    More maintainable then some other solution?                                                                                         
                                                                                                                                        
    I have a template two messy datasets                                                                                                
                                                                                                                                        
    related to                                                                                                                          
    https://tinyurl.com/y7vwe75w                                                                                                        
    https://communities.sas.com/t5/SAS-Programming/Dynamically-change-the-name-of-variables/m-p/663671                                  
                                                                                                                                        
    *          _       _   _                                                                                                            
     ___  ___ | |_   _| |_(_) ___  _ __                                                                                                 
    / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                                
    \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                               
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                               
                                                                                                                                        
    ;                                                                                                                                   
                                                                                                                                        
    *_                   _                                                                                                              
    (_)_ __  _ __  _   _| |_                                                                                                            
    | | '_ \| '_ \| | | | __|                                                                                                           
    | | | | | |_) | |_| | |_                                                                                                            
    |_|_| |_| .__/ \__,_|\__|                                                                                                           
            |_|                                                                                                                         
    ;                                                                                                                                   
                                                                                                                                        
    * These are the final variable names;                                                                                               
    data template;                                                                                                                      
       retain s1 s2 s3 z1 z2 .;                                                                                                         
    run;quit;                                                                                                                           
                                                                                                                                        
    /*                                                                                                                                  
    WORK.TEMPLATE total obs=1                                                                                                           
                                                                                                                                        
    Obs    s1    s2    s3    z1    z2                                                                                                   
                                                                                                                                        
     1      .     .     .     .     .                                                                                                   
    */                                                                                                                                  
                                                                                                                                        
    data hav001;                                                                                                                        
        s_oldpay=44;                                                                                                                    
        s_curpay=55;                                                                                                                    
        s_monpay=99;                                                                                                                    
        z_zip=12301;                                                                                                                    
        z_nextzip=18971;                                                                                                                
    run;quit;                                                                                                                           
                                                                                                                                        
    /*                                                                                                                                  
    WORK.HAV001 total obs=1                                                                                                             
                                                                                                                                        
      s_oldpay    s_curpay    s_monpay    z_zip    z_nextzip                                                                            
                                                                                                                                        
         44          55          99       12301      18971                                                                              
    */                                                                                                                                  
                                                                                                                                        
                                                                                                                                        
    data hav002;                                                                                                                        
        s_daypay=22;                                                                                                                    
        s_yearlsalary=33;                                                                                                               
        z_zipcode=14598;                                                                                                                
    run;                                                                                                                                
                                                                                                                                        
    /*                                                                                                                                  
    Up to 40 obs WORK.HAV002 total obs=1                                                                                                
                                                                                                                                        
      s_daypay    s_yearlsalary    z_zipcode                                                                                            
                                                                                                                                        
         22             33           14598                                                                                              
    */                                                                                                                                  
                                                                                                                                        
                                                                                                                                        
    *            _               _                                                                                                      
      ___  _   _| |_ _ __  _   _| |_                                                                                                    
     / _ \| | | | __| '_ \| | | | __|                                                                                                   
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                    
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                   
                    |_|                     | RULES ( the rub is that both do not need to exist                                         
    ;                                       |         and the position changes depending on how many s_ s                               
                                            | Rename                                                                                    
    WORK.WANT total obs=2                   | z_zip    z_nextzip                                                                        
                                            |                                                                                           
    Obs    s1    s2    s3      z1       z2  |  Z1          Z2                                                                           
                                            |                                                                                           
     1     44    55    99    12301    18971 | 12301      18971                                                                          
     2     22    33     .    14598        . |                                                                                           
                                                                                                                                        
    *          _       _   _                                                                                                            
     ___  ___ | |_   _| |_(_) ___  _ __                                                                                                 
    / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                                
    \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                               
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                               
                                                                                                                                        
    ;                                                                                                                                   
                                                                                                                                        
    data template;                                                                                                                      
       retain s1 s2 s3 z1 z2 .;                                                                                                         
    run;quit;                                                                                                                           
                                                                                                                                        
    data hav001;                                                                                                                        
        s_oldpay=44;                                                                                                                    
        s_curpay=55;                                                                                                                    
        s_monpay=99;                                                                                                                    
        z_zip=12301;                                                                                                                    
        z_nextzip=18971;                                                                                                                
    run;quit;                                                                                                                           
                                                                                                                                        
    data hav002;                                                                                                                        
        s_daypay=22;                                                                                                                    
        s_yearlsalary=33;                                                                                                               
        z_zipcode=14598;                                                                                                                
    run;                                                                                                                                
                                                                                                                                        
    * solution;                                                                                                                         
    proc sql;                                                                                                                           
                                                                                                                                        
       * S_ variables;                                                                                                                  
       create table havs1 as select * from t(keep=s: obs=0) union select * from hav001(keep=s:);                                        
       create table havs2 as select * from t(keep=s: obs=0) union select * from hav002(keep=s:);                                        
                                                                                                                                        
       * z_ variables                                                                                                                   
       create table havz1 as select * from t(keep=z: obs=0) union select * from hav001(keep=z:);                                        
       create table havz2 as select * from t(keep=z: obs=0) union select * from hav002(keep=z:);                                        
                                                                                                                                        
    quit;                                                                                                                               
                                                                                                                                        
    data want;                                                                                                                          
                                                                                                                                        
       merge havs1 havz1;                                                                                                               
       output;                                                                                                                          
       merge havs2 havz2;                                                                                                               
       output;                                                                                                                          
                                                                                                                                        
    run;quit;                                                                                                                           
                                                                                                                                        
                                                                                                                                        
