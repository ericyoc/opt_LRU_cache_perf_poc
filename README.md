# Cache Replacement Algorithm Analsyis

This repository contains implementations and comparisons of different cache replacement algorithms, including Least Recently Used (LRU), First In First Out (FIFO), and Enhanced Not Recently Used (ENRU).

# Motivating Article
Gawanmeh, A., Abed, S., AlAwadh, S. A. A., Mansoor, W., Atalla, S., Alomari, A., & Yocam, E. (2023). Enhanced Not Recently Used Algorithm for Cache Memory Systems in Mobile Computing. Proceedings of the 2023 International Conference on Advances in Computing Research (ACR’23), 433–442. https://doi.org/10.1007/978-3-031-33743-7_35

## Algorithm Type

### Least Recently Used (LRU)

The Least Recently Used (LRU) algorithm is a popular cache replacement algorithm that keeps recently accessed items in the cache. It works by evicting the least recently used item when the cache reaches its capacity. LRU is widely used in various caching systems due to its simplicity and effectiveness in many scenarios.

### First In First Out (FIFO)

The First In First Out (FIFO) algorithm is a simple cache replacement algorithm that evicts items in the order they were inserted into the cache. FIFO does not consider the access patterns of the items and can potentially evict frequently accessed items. It is used in situations where access patterns are unknown or unpredictable.

### Enhanced Not Recently Used (ENRU)

The Enhanced Not Recently Used (ENRU) algorithm is a customized cache replacement algorithm that combines the benefits of LRU and FIFO. It divides the cache into three layers: top, middle, and bottom. The algorithm works as follows:

1. New items are inserted into the first location of the bottom layer.
2. When the cache reaches its capacity, items are replaced from the top layer using the ENRU algorithm.
3. Items are moved between layers based on their access patterns.

ENRU uses two bits associated with each item in the top layer: a reference bit (R) and a dirty bit (D). The priority for replacement is determined by the combination of these bits, with the order being: not referenced and not dirty, not referenced and dirty, referenced and not dirty, and referenced and dirty.

## Performance Comparison

The performance of each algorithm is evaluated using different access patterns: default and conditional. The default access pattern represents a scenario with a low skew factor, while the conditional access pattern represents a scenario with a high skew factor.

| Algorithm                 | Performance (Default) | Performance (Conditional) |
|---------------------------|----------------------:|---------------------------:|
| Least Recently Used (LRU) |                 0.682 |                      0.975 |
| First In First Out (FIFO) |                 0.511 |                      0.487 |
| Enhanced Not Recently Used (ENRU) |         0.639 |                      0.992 |

The results show that ENRU outperforms LRU and FIFO in scenarios with conditional access patterns and limited cache capacity. ENRU achieves a higher hit ratio by effectively adapting to the access patterns and prioritizing the replacement of items based on their reference and dirty bits.

## Usage

To use the cache replacement algorithms in your project, you can simply import the corresponding classes (`LRUCache`, `FIFOCache`, `ENRUCache`) and create instances of the desired cache with a specified capacity. The `get` and `put` methods can be used to interact with the cache.

## Conclusion

The Enhanced Not Recently Used (ENRU) algorithm provides a powerful cache replacement strategy that combines the strengths of LRU and FIFO. By dividing the cache into layers and using reference and dirty bits, ENRU optimizes cache performance in scenarios with conditional access patterns and limited cache capacity. It outperforms traditional algorithms like LRU and FIFO in such scenarios, making it a valuable choice for caching systems with specific requirements.

Feel free to explore the code and adapt it to your needs. Contributions and feedback are welcome!

**Disclaimer**
This repository is intended for educational and research purposes.

## License
Copyright 2024 Eric Yocam

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
