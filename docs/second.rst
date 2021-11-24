.. _second-page:

*******************
Launching a pipeline
*******************

Nextflow supports a number of code sharing platforms: **BitBucket**, **GitHub**, and **GitLab**.
This feature allows to run pipelines by just pointing to an online repository without caring about downloading, installing etc. 
The default platform is **GitHub**, so we will use this repository as an example.

.. |github| image:: images/GitHub-Logo.png
  :width: 200

.. |bitbucket| image:: images/bitbucket-logo.png
  :width: 200
  
.. |gitlab| image:: images/gitlab-logo.jpeg
  :width: 200

.. list-table:: 
   :widths: 50 50 50
   :header-rows: 1

   * - GitHub
     - BitBucket
     - GitLab
   * - |github|
     - |bitbucket|
     - |gitlab|

We can launch the pipeline just by typing:

.. code-block:: console

  nextflow run lucacozzuto/elixir_NF -r main -latest -with-docker

In this way Nextflow will pull the pipeline from the GitHub repository, store it at ``$PATH/.nextflow/assets`` and launch it using the container engine `Docker <https://www.docker.com/>`__, thanks to the Nextflow parameter ``-with-docker``.

Nextflow supports many more container engines like Singularity, Shifter, Podman and Charliecloud. In this example we will use Docker: the default image is stored in `DockerHub <https://hub.docker.com/>`__ and is retrieved on the fly. 

.. code-block:: console

  N E X T F L O W  ~  version 21.04.3
  Pulling lucacozzuto/elixir_NF ...
  downloaded from https://github.com/lucacozzuto/elixir_NF.git
  Launching `lucacozzuto/elixir_NF` [determined_minsky] - revision: 711f9f806d [main]

  BIOCORE@CRG - N F TESTPIPE  ~  version 1.0
  =============================================
  reads                           : /Users/lcozzuto/.nextflow/assets/lucacozzuto/elixir_NF/data/*.fastq.gz
  reference                       : /Users/lcozzuto/.nextflow/assets/lucacozzuto/elixir_NF/data/chr19.fasta.gz
  output				: /Users/lcozzuto/.nextflow/assets/lucacozzuto/elixir_NF/output

  executor >  local (3)
  [2f/6cd1ca] process > fastqc (B7_H3K4me1_s_chr19.fastq.gz) [100%] 2 of 2 ✔
  [55/032373] process > BOWTIE:Index (chr19.fasta.gz)        [  0%] 0 of 1
  [79/f30f70] process > BOWTIE:Align (B7_H3K4me1_s_chr19.fastq.gz) [100%] 2 of 2 ✔
  [50/088302] process > multiqc                                    [100%] 1 of 1 ✔
  /Users/lcozzuto/ooo/work/27/f1cc39c1e01c9ee55684b347c492f5/B7_input_s_chr19.fastq.gz.sam
  /Users/lcozzuto/ooo/work/27/f1cc39c1e01c9ee55684b347c492f5/B7_input_s_chr19.fastq.gz.log
  /Users/lcozzuto/ooo/work/79/f30f7041abf5baf7c496a0982906c1/B7_H3K4me1_s_chr19.fastq.gz.sam
  /Users/lcozzuto/ooo/work/79/f30f7041abf5baf7c496a0982906c1/B7_H3K4me1_s_chr19.fastq.gz.log

  Done! Open the following report in your browser --> /Users/lcozzuto/.nextflow/assets/lucacozzuto/elixir_NF/output/ouptut_multiQC/multiqc_report.html

  Completed at: 24-Nov-2021 15:48:35
  Duration    : 3m 25s
  CPU hours   : 0.1
  Succeeded   : 6

This pipeline can be launched also with Singularity just using the Nextflow parameter ``-with-singularity``. Nextflow will retrieve and convert the image(s) for you. The image(s) will be then stored so that next time you don't need to download anything again.


Reporting and monitoring
=========================
Before going to the code we can have a look 


