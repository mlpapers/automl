# Automatic Machine Learning (AutoML)

## Surveys

- **[AutoML principles and practices](https://arxiv.org/abs/1810.13306)** — 2018. Organizes automated learning by search space, search algorithm, and evaluation strategy, connecting pipeline configuration with architecture search and the underlying bilevel objective.
- **[AutoML survey](https://arxiv.org/abs/1908.00709)** — 2019. Reviews automation across data preparation, feature engineering, hyperparameter optimization, and neural architecture search; distinguishes one-shot search and joint architecture/hyperparameter optimization.
- **[Hyperparameter optimization survey](https://arxiv.org/abs/2007.15745)** — 2020. Compares optimization approaches for common learning algorithms, summarizes software, and discusses strengths, limitations, and unresolved research questions.

## Hyperparameter search

- **[Random search](https://www.jmlr.org/papers/v13/bergstra12a.html)** — 2012. Samples configurations instead of enumerating a grid. Its analysis explains why grids waste trials when only a few hyperparameters strongly affect validation performance.
- **[Sequential model-based optimization](https://proceedings.neurips.cc/paper/2011/hash/86e8f7ab32cfd12577bc2619bc635690-Abstract.html)** — 2011. Introduces sequential expected-improvement methods for conditional hyperparameter spaces, including tree-structured Parzen estimation; evaluates them against random search.
- **[Practical Bayesian optimization](https://arxiv.org/abs/1206.2944)** — 2012. Models validation performance with a Gaussian process and selects subsequent trials from its posterior; also considers variable evaluation costs and parallel experiments.
- **[Neural surrogates for Bayesian optimization](https://arxiv.org/abs/1502.05700)** — 2015. Uses a neural network to learn basis functions for Bayesian regression, replacing a Gaussian-process surrogate when many evaluations make its fitting cost restrictive.
- **[Hyperband](https://arxiv.org/abs/1603.06560)** — 2016. Allocates increasing resources to randomly sampled configurations and stops weak candidates early; searches across different tradeoffs between breadth and evaluation budget.
- **[BOHB](https://arxiv.org/abs/1807.01774)** — 2018. Combines model-guided configuration selection with Hyperband's budget allocation, joining informed search with evaluations at multiple resource levels.
- **[ASHA](https://arxiv.org/abs/1810.05934)** — 2018. Uses asynchronous resource allocation and aggressive early stopping for parallel hyperparameter tuning, allowing search to exploit many workers without synchronized evaluation rounds.

## Pipeline search and ensembles

- **[Auto-sklearn](https://proceedings.neurips.cc/paper/2015/hash/11d0e6287202fced83f79975ec59a3a6-Abstract.html)** — 2015. Combines Bayesian pipeline search with learning from previous datasets and ensembles of evaluated models; jointly selects preprocessing, classifiers, and hyperparameters.
- **[Auto-sklearn 2.0](https://arxiv.org/abs/2007.04074)** — 2020. Adds portfolio-based meta-learning and bandit budget allocation, then selects among AutoML strategies to reduce the configuration burden on users.
- **[Auto-PyTorch](https://arxiv.org/abs/2006.13799)** — 2020. Jointly optimizes network architecture and training hyperparameters using multiple evaluation budgets, portfolio warm starts, and ensembles with tabular baselines; introduces LCBench learning curves.
- **[AutoGluon-Tabular](https://arxiv.org/abs/2003.06505)** — 2020. Builds multilayer stacked ensembles for tabular prediction, emphasizing combinations of models rather than spending the entire budget on selecting one configuration.
- **[FLAML](https://arxiv.org/abs/1911.04706)** — 2019. Adapts learner and hyperparameter search to trial cost and model error, using resource-aware search strategies for tabular AutoML under limited computation budgets.
- **[AlphaD3M](https://arxiv.org/abs/1905.10345)** — 2019. Uses a pipeline grammar and model-based reinforcement learning with pretrained guidance to synthesize classification and regression pipelines; the paper reports public code, models, and data.
- **[AutoML-DSGE](https://arxiv.org/abs/2004.00307)** — 2020. Evolves scikit-learn classification pipelines with Dynamic Structured Grammatical Evolution, constraining candidate pipelines through a grammar.
- **[GAMA](https://arxiv.org/abs/2007.04911)** — 2020. Provides modular pipeline-search and post-processing components with logging and visualization, supporting controlled comparisons between AutoML strategies.
- **[Lale](https://arxiv.org/abs/2007.01977)** — 2020. Unifies manual and automated pipeline construction through high-level Python interfaces, including topology search, higher-order operators, and consistency checks.
- **[VolcanoML](https://arxiv.org/abs/2107.08861)** — 2021. Decomposes large pipeline-search spaces into smaller searches and composes them into execution plans, separating search-space structure from optimization execution.

## Pretrained models and agent-driven automation

- **[TabPFN](https://www.nature.com/articles/s41586-024-08328-6)** — 2025. Pretrains on synthetic prediction tasks, then conditions predictions on a labeled table. Amortizes learning across datasets; the paper evaluates small tables up to 10,000 rows, not unrestricted tabular prediction.
- **[MLZero](https://arxiv.org/html/2505.13941)** — 2025. Uses data-inspection agents, library knowledge and execution history to generate and revise ML pipelines. Evaluated on MLE-bench Lite and an author-created multimodal benchmark. [Code](https://github.com/autogluon/autogluon-assistant).

## Neural architecture search

- **[Reinforcement-learning NAS](https://arxiv.org/abs/1611.01578)** — 2016. Trains a recurrent controller to generate network descriptions, using candidate validation accuracy as a reinforcement-learning reward.
- **[Regularized evolution](https://arxiv.org/abs/1802.01548)** — 2018. Uses tournament-based architecture evolution with an age preference for younger candidates; studies search efficiency through controlled comparisons with reinforcement learning.
- **[ENAS](https://arxiv.org/abs/1802.03268)** — 2018. Searches for subgraphs of a shared computation graph. Parameter sharing amortizes candidate training, while a policy-gradient controller selects architectures using validation rewards.
- **[DARTS](https://arxiv.org/abs/1806.09055)** — 2018. Continuously relaxes discrete architecture choices so gradients can optimize the search representation, replacing evolutionary or reinforcement-learning search over discrete candidates.
- **[Petridish](https://arxiv.org/abs/1905.13360)** — 2019. Grows networks by adding shortcut connections, motivated by forward stage-wise regression and gradient boosting; jointly trains candidate connections before selecting a subset.
- **[AgEBO-Tabular](https://arxiv.org/abs/2010.16358)** — 2020. Combines aging evolution for architectures with asynchronous Bayesian tuning of data-parallel training settings, jointly adapting network structure and training configuration.
- **[MnasNet](https://arxiv.org/abs/1807.11626)** — 2018. Searches mobile architectures using both accuracy and measured device latency in its objective; hardware measurements replace operation counts as the deployment-cost signal.
- **[Zero-cost NAS proxies](https://arxiv.org/abs/2101.08134)** — 2021. Ranks candidate architectures using inexpensive initialization-time scores, including pruning-inspired proxies computed from one minibatch; proxy rankings still require validation against trained models.

## Model structure and algorithm discovery

- **[Compositional kernel search](https://arxiv.org/abs/1302.4922)** — 2013. Searches Gaussian-process kernels built from sums and products of elementary kernels, yielding decompositions of regression functions into interpretable components.
- **[Automatic statistician](https://arxiv.org/abs/1402.4304)** — 2014. Searches compositional Gaussian-process regression models and generates figures and natural-language descriptions of trends, periodicity, and changepoints.
- **[AutoML-Zero](https://arxiv.org/abs/2003.03384)** — 2020. Evolves learning programs from basic mathematical operations, searching model structure and learning rules together; demonstrations use constrained tasks rather than unrestricted autonomous research.

## Evaluation

- **[NAS-Bench-101](https://arxiv.org/abs/1902.09635)** — 2019. Provides repeated evaluations of a fixed convolutional architecture space on CIFAR-10, allowing reproducible search comparisons through table queries rather than retraining each candidate.
- **[NAS-Bench-201](https://arxiv.org/abs/2001.00326)** — 2020. Records training results for all 15,625 cells in a fixed search space on three datasets. Enables controlled comparisons of search algorithms; ranking performance within this space does not establish superiority across architectures or training recipes.
- **[Random-search NAS baselines](https://arxiv.org/abs/1902.07638)** — 2019. Li and Talwalkar find early-stopped random search competitive with ENAS on PTB and CIFAR-10. Weight sharing improves their baseline further; comparisons need repeated runs, matched training recipes and explicit search cost.
- **[AMLB](https://arxiv.org/abs/2207.12560)** — 2022. Benchmarks AutoML systems across classification and regression tasks, measuring predictive quality, inference time, and failures; task subsets can produce different framework rankings.
- **[Budget-sensitive AutoML evaluation](https://arxiv.org/html/2504.01222)** — 2025. Across 104 tasks, framework rankings remain fairly stable as time budgets shrink, including to five minutes. Early stopping has more varied effects; results concern the tested versions and configurations.
- **[MLE-bench](https://arxiv.org/abs/2410.07095)** — 2024. Benchmarks agents on ML competitions requiring data preparation, model training and experimental iteration; examines resource limits, pretraining contamination and grading against competition metrics.
- **[AutoML stopping protocols](https://arxiv.org/html/2504.01222)** — The study mixes model-level stopping, generation-based search stopping and ensemble callbacks across frameworks. These controls stop different computations; identical patience values do not imply comparable resource budgets.
- **[TabArena](https://arxiv.org/html/2506.16791v4)** — 2025. Curates IID tabular tasks and compares defaults, tuning and ensembles. The best deep models match or beat boosted trees with tuning and ensembling at larger budgets; foundation models cover subsets in this paper snapshot.
- **[CARPS](https://arxiv.org/html/2506.06143)** — 2025. Connects optimizers to black-box, multi-fidelity and multi-objective benchmarks through one interface. Selects representative task subsets to reduce evaluation cost; records trajectories for analysis. [Code](https://github.com/automl/CARP-S).
- **[Test-time compute for tabular models](https://arxiv.org/html/2610.12005)** — 2026 preprint. On TabArena, greedy selection improves TabPFN-3 while uniform averaging of the same 96 configurations worsens error. Selection gains shrink when fewer out-of-fold labels guide the ensemble.

## Optimization and experiment software

- **[Hyperopt](https://proceedings.scipy.org/articles/Majora-8b375195-003)** — 2013. Describes search-space specification, sequential model-based optimization, and parallel execution in Python, with analysis of completed tuning trials.
- **[Optuna](https://optuna.readthedocs.io/en/stable/)** — Defines conditional search spaces in Python; samplers propose parameters and pruners stop unpromising trials. Supports parallel studies and inspection of trial histories. [Paper](https://arxiv.org/abs/1907.10902).
- **[SMAC3](https://automl.github.io/SMAC3/latest/)** — Bayesian optimization for conditional configuration spaces, multiple fidelities, objectives and problem instances. Provides ask-and-tell and warm-start interfaces. [Paper](https://arxiv.org/abs/2109.09831).
- **[Ray Tune](https://arxiv.org/abs/1807.05118)** — 2018. Separates training scripts from model-selection algorithms through a common interface, supporting distributed search and scheduling across compute clusters.
- **[Katib](https://arxiv.org/abs/2006.02085)** — 2020. Presents a framework-agnostic tuning service designed around scalability, fault tolerance, extensibility, and multiple users in cloud-native deployments.
- **[Mango](https://arxiv.org/abs/2005.11394)** — 2020. Provides parallel hyperparameter tuning over mixed search spaces, separating search strategy from distributed scheduling and handling failed evaluations.
- **[PHS](https://arxiv.org/abs/2002.11429)** — 2020. Distributes hyperparameter searches for arbitrary Python functions across compute instances; uses Bayesian optimization to select queries for expensive evaluations.
- **[Ax](https://ax.dev/)** — Adaptive experimentation platform for defining, managing, and running optimization studies, including field experiments.
- **[BoTorch](https://botorch.org/docs/introduction.html)** — PyTorch library for Bayesian optimization research; integrates with Ax for experiment management and data handling.
- **[RoBO](https://github.com/automl/RoBO)** — Research framework for Bayesian optimization with Gaussian-process and random-forest dependencies; the repository includes installation instructions and its original framework paper.
- **[Auptimizer](https://lge-arc-advancedai.github.io/auptimizer/)** — Coordinates hyperparameter and model-compression experiments, records results, and includes model-conversion tooling for deployment.
- **[Talos](https://github.com/autonomio/talos)** — Runs parameter experiments around user-supplied Keras, TensorFlow or PyTorch models, recording histories and recovering selected models. Talos 2 and the supported 1.x series have separate APIs and environment requirements.
- **[KerasTuner](https://keras.io/keras_tuner/)** — Defines hyperparameters during model construction and searches them with Bayesian optimization, Hyperband, or random search.
- **[HyperparameterHunter](https://hyperparameter-hunter.readthedocs.io/en/latest/)** — Documentation for experiment environments, hyperparameter spaces, optimization, and feature-engineering interfaces.

## Pipeline and domain software

- **[TPOT](https://epistasislab.github.io/tpot/latest/)** — Optimizes machine-learning pipelines through genetic programming; its graph-based rewrite supports flexible search spaces and multiple optimization objectives.
- **[AutoKeras](https://autokeras.com/)** — Keras-based AutoML interfaces for fitting models from data, with task-specific estimators and architecture search.
- **[H2O AutoML](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/automl.html)** — Automates supervised model training and tuning in H2O, including ensembles of candidate models.
- **[AutoGBT](https://github.com/flytxtds/AutoGBT)** — Automatically tunes gradient-boosted trees for streaming classification under concept drift; developed for the lifelong AutoML challenge.
- **[AutoGBT-alt](https://github.com/pfnet-research/autogbt-alt)** — Experimental AutoGBT reimplementation using LightGBM and Optuna, with feature processing, sampling, and cross-validated tuning.
- **[AutoRec](https://github.com/datamllab/AutoRec)** — Keras-based automated recommendation toolkit with architecture search for rating prediction and click-through-rate tasks.
- **[AutoViML](https://github.com/AutoViML/Auto_ViML)** — Automates predictive-model construction and associated feature processing; exposes configuration for model selection and analysis.
- **[automl-gs](https://github.com/minimaxir/automl-gs/)** — Builds prediction models from a CSV and target column and exports Python pipelines so preprocessing and modeling steps can be inspected and adapted.
- **[Ludwig](https://github.com/ludwig-ai/ludwig)** — Declarative framework for training and fine-tuning models from configuration files, including language, multimodal, and tabular models.
- **[MLBox](https://mlbox.readthedocs.io/en/latest/)** — Combines preprocessing, feature selection, hyperparameter optimization, and classification/regression models, including stacking.
- **[TransmogrifAI](https://github.com/salesforce/TransmogrifAI)** — Scala AutoML library on Apache Spark, organizing reusable machine-learning workflows with compile-time type checking.
- **[AutoGluon](https://auto.gluon.ai/stable/index.html)** — Pipeline interfaces for tabular, time-series and multimodal prediction. Tabular presets combine conventional learners and pretrained models; model choices, hardware needs and checkpoint licenses vary by preset.
- **[FLAML](https://microsoft.github.io/FLAML/docs/Use-Cases/Task-Oriented-AutoML/)** — Searches learners and configurations under time or trial budgets, with optional stacked ensembles. Supports prediction-time and custom metric constraints; search cost and deployment constraints are separate controls.

## Archived and legacy implementations

- **[NNI](https://github.com/microsoft/nni)** — Toolkit for hyperparameter search, neural architecture search and model compression. Microsoft archived the repository in September 2024; preserved documentation describes the archived implementation.
- **[AdaNet](https://github.com/tensorflow/adanet)** — TensorFlow framework combining neural-subnetwork growth with ensemble learning. The repository was archived in April 2026; the method remains a research reference, while this implementation is read-only.
- **[Milano](https://github.com/nvidia/Milano)** — Runs parameter searches against training scripts on configurable compute backends. NVIDIA archived the repository in August 2021; retained as a historical orchestration implementation.
- **[HpBandSter](https://github.com/automl/HpBandSter)** — Distributed Hyperband/BOHB implementation. Maintainers explicitly state that it is no longer maintained and point to SMAC3 and DEHB as successors; retain for historical reproduction.
- **[Spearmint](https://github.com/HIPS/Spearmint)** — Bayesian optimization implementation whose setup documents Python 2.7. This repository uses an academic/non-commercial research license; the separate older implementation has different terms.
- **[RECIPE](https://github.com/laic-ufmg/Recipe)** — Uses grammar-based genetic programming to evolve classification pipelines; the original implementation documents a Python 2.7 environment.

## Related Topics

- [Optimization](https://mlpapers.org/optimization/)
- [Neural Networks](https://mlpapers.org/neural-nets/)
- [Ensemble Learning](https://mlpapers.org/ensemble-learning/)
- [Feature Selection](https://mlpapers.org/feature-selection/)
