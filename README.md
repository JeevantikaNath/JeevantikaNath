- 👋 Hi, I’m @JeevantikaNath
- 👀 I’m interested in Data Science
- 🌱 I’m currently learning BCA from SRM University
- import pandas as pd
import matplotlib.pyplot as plt
import os

# Load the dataset
def load_data(file_path):
    return pd.read_csv(file_path)

# Create a bar chart for each country
def plot_country_data(df, country, output_dir):
    country_df = df[df['country'] == country]
    plt.figure(figsize=(8, 6))
    plt.bar(country_df['age'], country_df['frequency'], color='skyblue', edgecolor='black')
    plt.title(f'Age Distribution in {country}')
    plt.xlabel('Age')
    plt.ylabel('Frequency')
    plt.grid(axis='y', linestyle='--', alpha=0.7)
    plt.tight_layout()
    
    # Save the figure
    plt.savefig(f'{output_dir}/{country}_age_distribution.png')
    plt.close()

# Create a combined graph for all countries
def plot_combined_data(df, output_dir):
    plt.figure(figsize=(12, 8))
    for country in df['country'].unique():
        country_df = df[df['country'] == country]
        plt.plot(country_df['age'], country_df['frequency'], label=country)

    plt.title('Age Distribution Across 190 Countries')
    plt.xlabel('Age')
    plt.ylabel('Frequency')
    plt.legend(loc='upper right')
    plt.grid(axis='y', linestyle='--', alpha=0.7)
    plt.tight_layout()
    
    # Save the figure
    plt.savefig(f'{output_dir}/combined_age_distribution.png')
    plt.close()

# Main function to process all data
def main():
    # Load the data
    country_data = load_data('data/country_data.csv')
    combined_data = load_data('data/combined_data.csv')
    
    # Create output directory if not exists
    output_dir = 'output'
    os.makedirs(output_dir, exist_ok=True)
    
    # Plot individual country data
    for country in country_data['country'].unique():
        plot_country_data(country_data, country, output_dir)
    
    # Plot combined data
    plot_combined_data(combined_data, output_dir)

if __name__ == '__main__':
    main()


<!---
JeevantikaNath/JeevantikaNath is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
