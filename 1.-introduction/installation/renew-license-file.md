# Renew License File

### License already expired

If your license file is expired, the following error will pop out:

<figure><img src="../../.gitbook/assets/微信图片_20240805194951.png" alt=""><figcaption></figcaption></figure>

Please send us the Gudu SQLFlow Id (6 characters in red) and we will send you the renewed license file. Upload the renewd license file by click the "upload license file" link.

### Renewing a license before it expires

In case you wish to renew a license before it expires to avoid any impact of use, you can either directly update the license file `gudu_sqlflow_license.txt` or upload the license on the web page.

#### Option1: Upload the license on the web

Click the Information button in the left toolbar:

<figure><img src="../../.gitbook/assets/微信图片_20240806215554.png" alt=""><figcaption></figcaption></figure>

Upload the new license file with `Upload License File`:

<figure><img src="../../.gitbook/assets/微信图片_20240806215615.png" alt=""><figcaption></figcaption></figure>

#### Option2: Replace the license file directly

The following folder contains SQLFlow license file:

```
/wings/sqlflow/backend/conf
```

Windows users can find the license file under&#x20;

```
C:\wings\sqlflow\backend\conf
```

You can directly replace the license file under the folder. Please make sure the license has the correct access. You can use the following command to to grant the access for the license file:

```bash
sudo chmod 755 gudu_sqlflow_license.txt
```

Once updated, please restart the SQLFlow.
