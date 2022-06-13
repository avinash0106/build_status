#!/groovy

import com.opencsv.CSVReader
import com.opencsv.CSVWriter

node {
  try {
  if (CSVReader reader = new CSVReader(new FileReader("sample.csv")))
{
  String [] nextLine;

//here you can ask for next build job number
function getNextBuildNr(){
  curl --silent nextLine/api/json | grep -Po '"nextBuildNumber":\K\d+'
}    

// this will request the Status of job
function getBuildState(){
  buildNr=$1
  curl --silent nextLine/api/json | grep -Po '"result":\s*"\K\w+'

}

  //Read one line at a time
  while ((nextLine = reader.readNext()) != null)
  {
    //Use the tokens as required
    System.out.println(Arrays.toString(nextLine));
  }
}
catch (IOException | CsvValidationException e) {
  e.printStackTrace();
}
}
