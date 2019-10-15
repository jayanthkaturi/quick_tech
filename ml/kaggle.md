```python
import missingno as msno
import seaborn as sns
import matplot.pyplot as plt

## missing data analysis helpers
msno.bar(df.sample( 18207 ),(28,10),color='green') ## a bar plot
msno.matrix(df,color=(0.2,0,0.9)) ## missing data as white lines 
df[col].value_counts()

## correlation heat map
colormap = plt.cm.RdBu
plt.figure(figsize=(14,12))
plt.title("Pearson Coefficient")
sns.heatmap(train_df.corr(), cmap=colormap, annot=True)

## bar plots
plt.figure(figsize=(20, 10))
plt.bar(decks, deck_vs_sur.Survived.values, label='Survived')
plt.bar(decks, deck_vs_sur.NotSurvived.values, bottom=deck_vs_sur.Survived.values, label='Not Survived')
plt.legend(loc='upper left', bbox_to_anchor=(1, 1), prop={'size': 15})

## dist plots
sns.distplot(all_df[all_df['Survived'] == 1]['Age'], label='Survived')
sns.distplot(all_df[all_df['Survived'] != 1]['Age'], label='NotSurvived')
plt.show()

## count plots
cat = ['Embarked', 'Parch', 'Pclass', 'Sex', 'SibSp', 'Deck', 'FamilyCount', 'IsAlone']
plt.subplots(ncols=2, nrows=4, figsize=(20,10))
for i,c in enumerate(cat, 1):
    plt.subplot(2, 4, i)
    sns.countplot(x=c, hue='Survived', data=all_df)
    plt.legend(loc='upper right')
plt.show()

## pair plots
g = sns.pairplot(iris, hue="species", palette="husl", height=3, kind="reg", diag_kind="kde")

## continous
## log transformation
## df[col] = pd.qcut(df[col], 4)

## Categorical
## merge features
## from sklearn.preprocessing import LabelEncoder, StandardScaler
## LabelEncoder().fit_transfrom(df[col])
## StandardScaler().fit_transfrom(df[col])

"""
1. Exploratory Data Analysis

    1.1. Overview
    1.2. Dealing with Missing Values
        1.2.1. Age
        1.2.2. Embarked
        1.2.3. Fare
        1.2.4. Cabin
    1.3. Survival Distribution
    1.4. Correlations
    1.5. Survival Distribution in Features
        1.5.1. Continuous Features
        1.5.2. Categorical Features
    1.6. Conclusion

2. Feature Engineering

    2.1. Binning the Continuous Features
        2.1.1. Fare
        2.1.2. Age
    2.2. Family Size & Ticket Frequency
    2.3. Title & Is Married
    2.4. Family Survival Rate & Ticket Survival Rate
    2.5. Feature Transformation
        2.5.1. Label Encoding the Non-Numerical Features
        2.5.2. One-Hot Encoding the Categorical Features
    2.6. Conclusion
"""

## https://www.kaggle.com/gunesevitan/advanced-feature-engineering-tutorial-with-titanic
## https://www.kaggle.com/arthurtok/introduction-to-ensembling-stacking-in-python
```
