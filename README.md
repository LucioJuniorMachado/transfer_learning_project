# transfer_learning_project
This is a project from BairesDev - Machine Learning Practitioner bootcamp

Transfer learning and fine-tuning

Download de dados
Usei um conjunto de dados contendo vários milhares de imagens de cães e gatos. Fiz download e extraí um arquivo zip contendo as imagens e crie um tf.data.Dataset para treinamento e validação usando o utilitário tf.keras.utils.image_dataset_from_directory .

Mostrei as primeiras nove imagens e rótulos do conjunto de treinamento.

Como o conjunto de dados original não contém um conjunto de teste, criei um. Para fazer isso, determinei quantos lotes de dados estão disponíveis no conjunto de validação usando tf.data.experimental.cardinality e movi 20% deles para um conjunto de teste.

Configurei o conjunto de dados para desempenho.

Usei o data_augmentation.

Redimensionei valores de pixel.

Criei o modelo base a partir dos convnets pré-treinados.

Congelei a base convolucional.

Adicionei um cabeçalho de classificação.

Compilei o modelo antes de treiná-lo.

Treinei o modelo.

Dei uma olhada nas curvas de aprendizado.

Descongelei as camadas superiores do modelo.

Compilei novamente o modelo e continuei treinando com o fine_tune.

Após o ajuste fino o modelo atingiu quase 98% de precisão no conjunto de validação.

Fiz uma avaliação e predição.

Resumo
Usei um modelo pré-treinado para extração de recursos : ao trabalhar com um conjunto de dados pequeno, é uma prática comum aproveitar os recursos aprendidos por um modelo treinado em um conjunto de dados maior no mesmo domínio. Isso é feito instanciando o modelo pré-treinado e adicionando um classificador totalmente conectado no topo. O modelo pré-treinado é "congelado" e apenas os pesos do classificador são atualizados durante o treinamento. Nesse caso, a base convolucional extraiu todos os recursos associados a cada imagem e eu acabei de treinar um classificador que determina a classe da imagem a partir desse conjunto de recursos extraídos.

Ajustando um modelo pré-treinado : para melhorar ainda mais o desempenho, pode-se querer redirecionar as camadas de nível superior dos modelos pré-treinados para o novo conjunto de dados por meio de ajuste fino. Nesse caso, ajustei meus pesos para que meu modelo aprendesse recursos de alto nível específicos para o conjunto de dados. Essa técnica geralmente é recomendada quando o conjunto de dados de treinamento é grande e muito semelhante ao conjunto de dados original no qual o modelo pré-treinado foi treinado.



