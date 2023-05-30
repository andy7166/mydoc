import matplotlib.pyplot as plt

class DataVisualizer:
    def __init__(self, data):
        self.data = data

    def plot_feature_distributions(self):
        for feature in self.data[0].keys():
            values = [d[feature] for d in self.data]

            fig, ax = plt.subplots()
            ax.hist(values, bins=10, edgecolor='black')
            ax.set_xlabel(feature)
            ax.set_ylabel('Frequency')
            ax.set_title(f'{feature} Feature Distribution')
            plt.show()
