# EGA-tricks
tricks to use the European Genome-Phenome Archive from the European Bioinformatics Institute

## Downloading data from the EGA API
- Download the EGA client at https://www.ebi.ac.uk/ega/sites/ebi.ac.uk.ega/files/documents/EGA_download_client_2.2.2.zip
- Downloading the data using the EGA client requires 3 steps

### 1. Requesting the dataset or files
To request the dataset with ID EGADXXXXXXXXXXXX, type
```bash
java -jar EgaDemoClient.jar -p <email> <password> -rfd EGADXXXXXXXXXXXX -re abc -label request_EGADXXXXXXXXXXXX
```
where <email> and <password> are the login and password of your EGA account, -re enables to specify an encryption key (here 'abc'), and -label enables to specify the request label that will be used to download the data.

To request the data file with ID EGAFXXXXXXXXXXXX, type
```bash
java -jar EgaDemoClient.jar -p <email> <password> -rf	EGAFXXXXXXXXXXXX -re abc -label request_EGAFXXXXXXXXXXXX
```

### 2. Downloading the encrypted dataset
To download the request (either a dataset or a file), type
 ```bash
java -jar EgaDemoClient.jar -p <email> <password> -dr request_EGAXXXXXXXXXXXXX -nt 4
```
where -nt enables to specify the number of parallel download streams (the more the faster the download).

### 3. Decrypting the encrypted files
To decrypt the downloaded files, type
```bash
java -jar EgaDemoClient.jar -p <email> <password> -dc <path to file1> <path to file2> -dck abc
```
where -dck enables to specify the encryption key (should match that given in step 1).
