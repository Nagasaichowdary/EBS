# WORKING WITH EBS
## NAME: POPURI ADITYA NAGA SAI
## REG NO: 212223110036

## Aim

To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

---

## Algorithm / Steps

1. Create a new Amazon EBS volume with a size of 1 GiB.
2. Select the same Availability Zone as the EC2 instance.
3. Attach the EBS volume to the EC2 instance using `/dev/sdb`.
4. Connect to the EC2 instance using AWS Systems Manager Session Manager.
5. Check the available storage using `df -h`.
6. Create an `ext3` file system on the EBS volume.
7. Create the `/mnt/data-store` directory.
8. Mount the EBS volume to `/mnt/data-store`.
9. Configure `/etc/fstab` for automatic mounting.
10. Verify that the EBS volume is successfully mounted.
11. Create `file.txt` inside the mounted EBS volume.
12. Verify the contents of the created file.
13. Create an EBS snapshot named `My Snapshot`.
14. Delete `file.txt` from the original EBS volume.
15. Create a new EBS volume from the snapshot.
16. Attach the restored volume to the EC2 instance using `/dev/sdc`.
17. Create the `/mnt/data-store2` directory.
18. Mount the restored volume to `/mnt/data-store2`.
19. Verify that `file.txt` has been successfully restored.

---

## Program

### 1. Check Available Storage

```bash
df -h
```

### 2. Create an ext3 File System

```bash
sudo mkfs -t ext3 /dev/sdb
```

### 3. Create a Mount Directory

```bash
sudo mkdir /mnt/data-store
```

### 4. Mount the EBS Volume

```bash
sudo mount /dev/sdb /mnt/data-store
```

### 5. Configure Automatic Mounting

```bash
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```

### 6. View the File System Configuration

```bash
cat /etc/fstab
```

### 7. Verify the Mounted Volume

```bash
df -h
```

### 8. Create a File in the EBS Volume

```bash
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```

### 9. Read the File

```bash
cat /mnt/data-store/file.txt
```

### 10. Delete the File

```bash
sudo rm /mnt/data-store/file.txt
```

### 11. Verify File Deletion

```bash
ls /mnt/data-store/
```

### 12. Create a Mount Directory for the Restored Volume

```bash
sudo mkdir /mnt/data-store2
```

### 13. Mount the Restored EBS Volume

```bash
sudo mount /dev/sdc /mnt/data-store2
```

### 14. Verify Snapshot Restoration

```bash
ls /mnt/data-store2/
```

Expected output:

```text
file.txt
```

---

## Outputs
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/83323d2e-810b-43b6-b6ba-5433d37ecc83" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5bd1897c-d472-4049-a1ae-a5b5eab9cd30" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/376db044-e2e8-4683-b1a2-a2d091066ca5" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7bdaee8f-c6b5-4fd2-97d6-bc262140c9db" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1989be3c-886a-4b02-b9f1-67104b28f424" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7098b92a-9b55-479d-917a-3970b832b260" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/67214d56-94be-4d29-877e-c1b07452f0ea" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2b0de040-6050-4693-90d7-757dc44b35e4" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/461d18a3-d823-4a24-9bc6-aa971ef7531c" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f20e70ab-af98-4d84-9db4-d56cda1bbe6d" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e3c331b6-0623-4eb1-8d4a-786fff879557" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/509c9de4-ab7f-46af-9858-f8f1d32d7b2e" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d8c2dd53-3b17-4adc-988e-e7c9e05acb77" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2460b590-21a9-439a-a5f0-46e49bb5eb0e" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/de3fe248-47a4-4c65-bf60-c0035edcabf6" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/97804407-d2b8-48d5-b941-7081f09d1b0f" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/88230e11-324b-41bb-b599-bddd33bb0d86" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/59ae2ad1-ae03-49d8-9ee8-b820557cda47" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/22e77cb2-fd3e-4bbd-b1ad-9e221cf92582" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2914bc8d-3d44-43ec-bbf8-141566f4a2ae" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ce8abf45-9c3d-4f6f-bcc7-3a30e5fd37fb" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4a7db5ba-4ee2-478e-abdc-58c03f10f948" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9261c808-683f-44c2-af78-a623462b3e2c" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7ba301d6-9c0c-4b24-86a0-085f826558b1" />


## Result
Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.
