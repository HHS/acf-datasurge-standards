# Compute Considerations

Project work will be conducted across two primary environments: 1) Government Furnished Equipment (GFE) and 2) cloud contexts. Our GFE are equipped with 16 GB of RAM, a 235 GB SSD, and a 13th Gen Intel(R) Core(TM) i7-1365U processor at 1.80 GHz on a Windows 11 operating system.

## Optimizing GFE Performance

### Parallel and Serial Processing

Employ parallel and serial processing tactically to extract the most utility from the GFE.

#### Parallel Processing

For datasets that fit comfortably within the GFE RAM limits, consider processing in parallel. In the best cases, this can significantly reduce computation time by dividing the workload across multiple CPU cores. Parallel processing can be done in Python using libraries such as `dask`, and `pyspark`. In R, consider using packages such as `future` and `furrr` (a near drop-in replacement for the popular `purrr` package).

#### Serial Processing

Some datasets consist of many smaller files. For such data sets, even if their total size exceeds the available RAM on a GFE, processing each file in series can enable the work to be completed without moving to a cloud context.

### Other Strategies
- Data optimization: reduce the size of your dataset by filtering out irrelevant records.
- Efficient coding practices: Optimize your code by using vectorized operations, and efficient data structures. Consider using packages that are designed for speedy data processing such as `arrow`, `dtplyr`, and `data.table` in R and `pyspark` in Python.
- Memory management: Actively manage memory by freeing up unused variables, for example by explicitly calling `gc()` after removing large objects in R or `gc.collect()` in Python. Consider the use of data processing libraries that minimize memory footprint.
- Chunking: For large datasets, consider processing the data in chunks that fit into your RAM.

## Considering the Cloud

If the GFE context is underperforming consider the following factors before moving to the cloud:

### Size and Complexity of the Dataset

Datasets close to or exceeding the size of our available RAM may cause significant slowdowns or inability to process the data entirely in memory. If a dataset is larger than approximately 12GB (considering some memory for the operating system and other applications), it is time to consider switching to a cloud context.

### Cost 

Cloud services usually operate on a pay-as-you-go model, which can be cost-effective if your usage is variable. However, for consistent usage, the costs can add up. Local development might require an upfront investment in hardware or software but can be cheaper in the long run. If the software needed for the project is locally available and there are no other concerns that make moving to the cloud desirable, consider conducting the work on a GFE.

### Scalability 

If the project is expected to grow rapidly, or the amount of resources needed will vary throughout the project's duration, consider using cloud services. Working in the cloud can provide the flexibility to scale resources up or down quickly and efficiently.

### Collaboration

Projects requiring collaboration, especially those with tasks involving sensitive data, may require at least some use of cloud services. Consider carefully what cloud services are needed. For example, if computational requirements are low but data must be shared, it may suffice to set up a database in the cloud.

### Security and Compliance

Carefully consider data security and compliance concerns when choosing the computing context. Cloud providers offer robust security measures, but some projects may require that sensitive data remain on-premises.

Cloud-based solutions must operate within environments that have been granted an Authority to Operate (ATO), ensuring they meet the comprehensive security standards required by the respective agency or department. 

Analyses performed on GFE must use  software that has been approved by HHS. This ensures that all data handling and processing activities are conducted safely, securely, and in compliance with federal regulations, thereby safeguarding sensitive information and maintaining the integrity of government operations.

### Performance
Some computationally intense tasks may require (or strongly benefit from) the use of a cloud environment. Keep in mind, however, the additional time required to configure and maintain the cloud environment. If the time savings outweigh the required investment, a cloud context may be a good choice.

### Making the Choice

The choice between cloud and local environments does not have to be a binary one. A hybrid approach, where some aspects of the project are handled locally and others in the cloud, is a possibility and may be more efficient than adopting either option entirely.