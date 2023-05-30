```
import matplotlib.pyplot as plt
import os

class DataVisualizer:
    def __init__(self, data):
        self.data = data

    def plot_feature_distributions(self, output_dir):
        os.makedirs(output_dir, exist_ok=True)
        
        for feature in self.data[0].keys():
            values = [d[feature] for d in self.data]

            fig, ax = plt.subplots()
            ax.hist(values, bins=10, edgecolor='black')
            ax.set_xlabel(feature)
            ax.set_ylabel('Frequency')
            ax.set_title(f'{feature} Feature Distribution')
            
            output_path = os.path.join(output_dir, f'{feature}_distribution.png')
            plt.savefig(output_path)
            plt.close()
    def plot_feature_distributions_ked(self, output_dir):
        os.makedirs(output_dir, exist_ok=True)
        
        for feature in self.data[0].keys():
            values = [d[feature] for d in self.data]

            # 使用核密度估计（KDE）平滑数据
            density = np.linspace(min(values), max(values), 1000)
            kde = gaussian_kde(values)
            smoothed_values = kde(density)
            
            fig, ax = plt.subplots()
            ax.plot(density, smoothed_values, color='blue')
            ax.fill_between(density, smoothed_values, color='lightblue')
            ax.set_xlabel(feature)
            ax.set_ylabel('Density')
            ax.set_title(f'{feature} Feature Distribution (Smoothed)')
            
            output_path = os.path.join(output_dir, f'{feature}_distribution.png')
            plt.savefig(output_path)
            plt.close()
            
            
```
