# QUIZ 1
`<04/07/2022>`

## 1. Which of the following types of blobs are designed to store text and binary data?

✔ **Block blob**

✖ Page blob

✖ Append blob

✖ Data blob

> NOTA: Data blob no existe

## 2. There are three access tiers for block blob data: hot, cold and archive. New storage accounts are created in which tier by default?

✔ **Hot (frecuente)**

✖ Cool (esporádico)

✖ Archive (archivo)

## 3. True or false, all data written to Azure Storage is automatically encrypted using SSL

✔ **False**

✖ True

> NOTA: Los datos están encriptados en reposo, pero para estar encriptados en tránsito tenemos que utilizar HTTPS. 
> SSL es un sistema de encriptación HTTPS. 

> NOTA: La pregunta hace referencia a todos los datos tanto en reposo como en tránsito, por tanto es falso

## 4. Which of the following types of blobs are used to store virtual hard drive files?

✔ **Page blobs**

✖ Block blobs

✖ Append blobs

> NOTA: los append blobs normalmente se usan para logs, es decir, para ir guardando datos incrementales

## 5. Which acces tier is considered to be offline and cannot be read or modified?

✔ **Archive**

✖ Cool

✖ Hot

## 6. Which of the following storage account types supports lifecycle policies?

✔ **General Purpose v2**

✖ General Purpose v1

✖ FileStorage

> NOTA: Las lifecycle policies son Hot, Cool y Archive

## 7. Which of the following classes of Azure Storage client library for .NET allows you to manipulate both Azure Storage containers and blobs?

✔ **BlobContainerClient**

✖ BlobClient

✖ BlobUriBuilder