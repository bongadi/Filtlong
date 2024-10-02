# Filtlong

**Filtlong**

**Filtlong Toolkit**
 
Filtlong is a tool used to filter long-read sequencing data based on quality scores, read length, and other user-defined parameters. It's particularly useful for long-read
sequencing technologies like PacBio and Oxford Nanopore, but it can also be applied to short-read data.
______________________________________________________________________________

**Key Features of Filtlong:**

   **Quality-based filtering** Keeps reads with the highest average quality scores.
    
   **Length-based filtering:** Removes shorter reads, keeping only those above a certain length.
    
   **Target base count:** Filters reads to keep a specified number of bases, useful when you want a specific coverage of the genome.
    
   **Percentage-based filtering:** Keeps a specified percentage of the highest-quality reads.
    
**Typical Use Cases:**

**Improving data quality:** Before alignment, assembly, or other downstream bioinformatics tasks, Filtlong can clean up raw sequencing data by removing low-quality or short reads.

**Reducing dataset size:** For very large datasets, you may want to reduce the number of reads while keeping the highest-quality ones for faster processing.



1.	Run wsl to access a **new terminal**.
By default, when you install Conda, a base environment is created and often activated unless you deactivate it or switch to another Conda environment. Therefore, you are likely to see that that the base Conda environment is currently active e.g.  (base) 
 
       ![image](https://github.com/user-attachments/assets/004205e1-5df5-4753-abb2-3a9ec57aa3a8)

2.	Identify the **path to the directory** you are currently in by using the command:  
                pwd
      You should be able see the path e.g.    /home/bongadi

       ![image](https://github.com/user-attachments/assets/7f0acdf2-d022-4d11-8e4a-845e62887ac2)


3.	Verify your **Conda installation** by running the command:     
       		Conda --version 
     	 You should see the installed version of Conda e.g. conda 24.7.1

       ![image](https://github.com/user-attachments/assets/6ceec7b9-6715-4831-b838-b8e4fb64ecf8)


4.	Create a **new environment in conda**: called **filtlong**.
          conda create -n filtlong

   	<img width="584" alt="image" src="https://github.com/user-attachments/assets/12ae9422-a2b4-45ad-b9db-50f74f82e0cc">

          
 
6.	**Activate** the filtlong environment.
               
          conda activate filtlong
  	
    <img width="522" alt="image" src="https://github.com/user-attachments/assets/9223bc4d-fbbd-4105-8c31-e3e8172ecb72">

       
  
8.	Install the **filtlong package** from the bioconda channel using Conda

         conda install –c bioconda filtlong
  	
  	   <img width="593" alt="image" src="https://github.com/user-attachments/assets/18f64e34-cca1-4272-89a0-a624b5535ab6">

      
9.	Basic usage of filtlong tools
   
    <img width="934" alt="image" src="https://github.com/user-attachments/assets/7d0770da-a49b-403d-a031-4c251e4c8da4">


    **--min_length:** Filters out reads shorter than the specified length.
  	
    **--keep_percent:** Keeps the top percentage of reads based on quality.
  	
    **input.fastq:** The input FASTQ file.
  	
    **output.fastq:** The output FASTQ file with filtered reads.

8.	List (**ls**) to check if you now have filtered reads

9.	**Advanced Options**
    
       --target_bases N: Filter reads down to N bases total (e.g., keep 100 million bases):
      
         filtlong --target_bases 100000000 input.fastq > output.fastq

     --min_mean_q: Set a minimum mean quality score for reads to be retained

        filtlong --min_mean_q 20 input.fastq > output.fastq

      --max_length: Remove reads longer than a specified length

        filtlong --max_length 50000 input.fastq > output.fastq


**Combining Filtlong with Other Tools:**

Filtlong can be part of a pre-processing pipeline that includes FastQC for quality control and tools like fastp or Trimmomatic for trimming and filtering.


  
