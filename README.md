# Project Overview
This repository contains a comprehensive exploratory data analysis on the cleaned Titanic dataset. It uncovers statistical patterns, demographic trends, and socio-economic factors influencing passenger survival rates using Python (Pandas, Matplotlib, Seaborn).

The main objective of this task is to perform an end-to-end exploratory analysis on the cleaned Titanic passenger dataset, compute summary statistics, and identify key demographic, economic, and behavioural patterns affecting passenger survival rates.
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

# Plot 1: Survival Rate by Class and Sex
sns.barplot(data=df, x='Pclass', y='Survived', hue='Sex', palette='Set2', ax=axes[0, 0])
axes[0, 0].set_title('1. Survival Rate by Class & Sex', fontsize=12, fontweight='bold')
axes[0, 0].set_ylabel('Survival Rate')

# Plot 2: Age Distribution by Survival
sns.kdeplot(data=df, x='Age', hue='Survived', common_norm=False, fill=True, palette='coolwarm', ax=axes[0, 1])
axes[0, 1].set_title('2. Age Distribution Density by Survival Status', fontsize=12, fontweight='bold')

# Plot 3: Survival Rate by Family Size
df['FamilySize'] = df['SibSp'] + df['Parch'] + 1
sns.barplot(data=df, x='FamilySize', y='Survived', palette='Blues_d', ax=axes[1, 0])
axes[1, 0].set_title('3. Survival Rate by Family Size', fontsize=12, fontweight='bold')
axes[1, 0].set_ylabel('Survival Rate')

# Plot 4: Log Fare Distribution by Survival
sns.boxplot(data=df, x='Survived', y='Fare', palette='Set3', ax=axes[1, 1])
axes[1, 1].set_yscale('log')
axes[1, 1].set_title('4. Fare Distribution (Log Scale)', fontsize=12, fontweight='bold')

plt.tight_layout()
plt.show()
