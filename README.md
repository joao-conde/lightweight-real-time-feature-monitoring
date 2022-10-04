# Lightweight Real-Time Feature Monitoring

Final submitted thesis document can be found here:

- Conde, J. (July 24, 2020). Master Thesis [*"Lightweight Real-Time Feature Monitoring"*](https://hdl.handle.net/10216/128535)

As a result of this master thesis project, two patents were made:

- WIPO Patent WO2022150062A1, filed July 28, 2021, and issued July 14, 2022. [*"Automated feature monitoring for data streams"*](https://patents.google.com/patent/WO2022150062A1/en)
- WIPO Patent WO2022150061A1, filed July 28, 2021, and issued July 14, 2022. [*"Generation of divergence distributions for automated data analysis"*](https://patents.google.com/patent/WO2022150061A1/en)

Additionally, one paper was submitted and presented at [KDD 2022](https://kdd.org/kdd2022/):
- Conde, J., Moreira, R., Torres, J., Cardoso, P., Ferreira, H., Sampaio, M., Ascensão, J., & Bizarro, P. (July 19, 2022). [*"Lightweight Automated Feature Monitoring for Data Streams"*](https://arxiv.org/abs/2207.08640)

## Abstract

Many real-time stream monitoring systems are static once deployed in a production environment. The engineers of those systems configure them under the assumption that future data flowing through the system roughly follows the same distribution as previously seen data. They do so consciously, to the best of their knowledge and available tools, keeping in mind that in the future they may need to reconfigure the system. Thus, even though the initial configuration of the system may be one of the best fits, over time, due to data pattern shifts, the initially deployed static system's performance gradually deteriorates. Data pattern shift detection refers to the process of finding patterns in data that do not conform to expected or usual behavior. Accurate and timely detection of data pattern deviations allows for immediate measures to be taken. Thus, the problem at hand is to determine when to reconfigure the system, *e.g.*, a Machine Learning model, based on an analysis of the drifts in the stream of data.

In this thesis, we design a method that makes use of lightweight streaming aggregations and distribution divergence functions to alert about deviations in data patterns in real-time, while in the presence of large volumes of high velocity, highly skewed and seasonal data. We develop a two-phased and two-windowed method: first, we perform a batch analysis on a reference window and then a stream analysis over a sliding streaming window. We aggregate the contents of both windows using an approximate histogram aggregation based on Exponential Moving Averages (EMAs). We do this for each event and each of its fields, also denominated features in our context. We measure the divergence between both reference and sliding window EMA-based histograms for each feature with the Jensen–Shannon Divergence function, but other distance functions could be used. For each feature, we find out the probability value of each divergence measure and apply the Holm-Bonferroni multiple test correction to find out which probability values are lowest and their associated features. We generate alerts based on a user-defined probability threshold, for each feature.

We evaluate our method through a series of tests, some with synthetic datasets and some with real data. We further split the tests into single and multi-feature analysis. Our method accurately detected the introduced anomalies in the experiments using synthetic datasets while maintaining high throughput, for single and multi-feature analysis. However, experiments with real data were not as accurate. Despite not knowing the specific reasons for that, we defer further investigation to future work and formulate a set of hypotheses that might explain it and hence are worthy of pursuing next. Our set of experiments supports the claim that sliding window aggregations and distribution divergence methods can be combined to detect data pattern shifts in streaming scenarios with constant time and memory complexity.
