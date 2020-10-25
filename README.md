# refactoring

## FlashGet
From Siravit's Covid-19-Tracker666 code: https://github.com/Kuea666/Covid-19-Tracker666

### initialize() Method
In the `src/cv19Tracker/homePageController.java ` class

https://github.com/Kuea666/Covid-19-Tracker666/blob/master/src/cv19Tracker/homePageController.java

consider this code :
```java
      @FXML
      void initialize() {
        Apane.setStyle("-fx-background-color: #4b5a81");//set background color.
        ReaderStrategy strategy=new ReadTextStrategy();
        String[] fromUrl= strategy.reader("http://covid19.th-stat.com/api/open/today");
        String dataConfirmed=fromUrl[0];//convert Confirmed to string
        String dataRecovered=fromUrl[1];//convert Recovered to string
        String dataHospitalized=fromUrl[2];//convert Hospitalized to string
        String dataDeath=fromUrl[3];//convert Death to string
        String dataNewConfirmed=fromUrl[4];//convert NewConfirmed to string
        String dataNewRecovered=fromUrl[5];//convert NewRecovered to string
        String dataNewHospitalize=fromUrl[6];//convert NewHospitalize to string
        String dataNewDeath=fromUrl[7];//convert NewDeath to string
        String dataDate=fromUrl[8];//convert Date to string

        lb1.setText(dataRecovered);//set Recovered
        lb2.setText(dataHospitalized);//set Hospitalized
        lb3.setText(dataDeath);//set Death
        lb4.setText(dataNewConfirmed);//set NewConfirmed
        lb5.setText(dataNewRecovered);//set NewRecovered
        lb6.setText(dataNewHospitalize);//set NewHospitalize
        lb7.setText(dataNewDeath);//set newDeath
        lb8.setText(dataConfirmed);//set Confirmed
        lb10.setText(dataDate);//set date

    }
```
* Refactoring Sign:

    * duplicate set text method
    
* Refactoring: create Enum for store values.

```java      
      @FXML
      void initialize() {
        Apane.setStyle("-fx-background-color: #4b5a81");//set background color.
        ReaderStrategy strategy=new ReadTextStrategy();
        String[] fromUrl= strategy.reader("http://covid19.th-stat.com/api/open/today");
        Label[] listLabel = new Label(){lb1, lb2, lb3,...,lb10};
        String data="";
        for(int i =0;listLabel.length;i++;){
          data=fromUrl[i];
          listLabel[1].setTest(data);
        }
        }
        
   
