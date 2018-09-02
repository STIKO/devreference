##Grant Container Engine Permission
**Error:** `required container.clusters.get permission for`

**Solution:**

Grant Kubernetes Engine IAM to the Container Builder service account:

    1. In GCP Console, visit the IAM menu.
    2. In the list of members, look for [YOUR-PROJECT-NUMBER]@cloudbuild.gserviceaccount.com.
    3. Click on the pencil icon in that row to grant a new role to that account.
    4. Click Add another role.
    5. Select Kubernetes Engine, then click Kubernetes Engine Admin.
    6. Click Save.
