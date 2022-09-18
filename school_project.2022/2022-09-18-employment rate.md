---
layout: single
title:  "취업률"
categories: jupyter
tag: [python, blog, jupyter]
toc: true
author_profile: false
---

<head>
  <style>
    table.dataframe {
      white-space: normal;
      width: 100%;
      height: 240px;
      display: block;
      overflow: auto;
      font-family: Arial, sans-serif;
      font-size: 0.9rem;
      line-height: 20px;
      text-align: center;
      border: 0px !important;
    }

    table.dataframe th {
      text-align: center;
      font-weight: bold;
      padding: 8px;
    }

    table.dataframe td {
      text-align: center;
      padding: 8px;
    }

    table.dataframe tr:hover {
      background: #b8d1f3; 
    }

    .output_prompt {
      overflow: auto;
      font-size: 0.9rem;
      line-height: 1.45;
      border-radius: 0.3rem;
      -webkit-overflow-scrolling: touch;
      padding: 0.8rem;
      margin-top: 0;
      margin-bottom: 15px;
      font: 1rem Consolas, "Liberation Mono", Menlo, Courier, monospace;
      color: $code-text-color;
      border: solid 1px $border-color;
      border-radius: 0.3rem;
      word-break: normal;
      white-space: pre;
    }

  .dataframe tbody tr th:only-of-type {
      vertical-align: middle;
  }

  .dataframe tbody tr th {
      vertical-align: top;
  }

  .dataframe thead th {
      text-align: center !important;
      padding: 8px;
  }

  .page__content p {
      margin: 0 0 0px !important;
  }

  .page__content p > strong {
    font-size: 0.8rem !important;
  }

  </style>
</head>



```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
```


```python
df1 = pd.read_excel('6-17.xlsx')
df2 = pd.read_excel('6-18.xlsx')
df3 = pd.read_excel('6-19.xlsx')
df4 = pd.read_excel('6-20.xlsx')
```


```python
#df5= new dataframe
df5 = pd.DataFrame([[2452,1016,1291,145, '52.65%'],
                   [2080, 837, 1143, 100, '54.95%'],
                   [1791,773, 897, 121, '50.08%'],
                   [1895, 847, 915, 133, '48.28%']],
                  columns = ['졸업자', '미취업자', '취업자', '그 외', '취업률'],
                  index = ['2017(2015.8~2016.2졸업자)', '2018(2016.8~2017.2졸업자)', '2019(2017.8~2018.2졸업자)', '2020(2018.8~2019.2졸업자)'])
df5
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>졸업자</th>
      <th>미취업자</th>
      <th>취업자</th>
      <th>그 외</th>
      <th>취업률</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017(2015.8~2016.2졸업자)</th>
      <td>2452</td>
      <td>1016</td>
      <td>1291</td>
      <td>145</td>
      <td>52.65%</td>
    </tr>
    <tr>
      <th>2018(2016.8~2017.2졸업자)</th>
      <td>2080</td>
      <td>837</td>
      <td>1143</td>
      <td>100</td>
      <td>54.95%</td>
    </tr>
    <tr>
      <th>2019(2017.8~2018.2졸업자)</th>
      <td>1791</td>
      <td>773</td>
      <td>897</td>
      <td>121</td>
      <td>50.08%</td>
    </tr>
    <tr>
      <th>2020(2018.8~2019.2졸업자)</th>
      <td>1895</td>
      <td>847</td>
      <td>915</td>
      <td>133</td>
      <td>48.28%</td>
    </tr>
  </tbody>
</table>
</div>



```python
import platform
import matplotlib.font_manager as fm

if platform.system() == 'Darwin': # Mac 환경 폰트 설정
    plt.rc('font', family='AppleGothic')
elif platform.system() == 'Windows': # Windows 환경 폰트 설정
    plt.rc('font', family='Malgun Gothic')
    
plt.rcParams['axes.unicode_minus'] = False #한글 폰트 사용시 마이너스 폰트 깨짐 해결
```


```python
df6 = pd.DataFrame([[52.65], [54.95], [50.08], [48.28]],
        columns = ['취업률'],
       index = ['2017(2015.8~2016.2)', '2018(2016.8~2017.2)', '2019(2017.8~2018.2)', '2020(2018.8~2019.2)'])
df6
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>취업률</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017(2015.8~2016.2)</th>
      <td>52.65</td>
    </tr>
    <tr>
      <th>2018(2016.8~2017.2)</th>
      <td>54.95</td>
    </tr>
    <tr>
      <th>2019(2017.8~2018.2)</th>
      <td>50.08</td>
    </tr>
    <tr>
      <th>2020(2018.8~2019.2)</th>
      <td>48.28</td>
    </tr>
  </tbody>
</table>
</div>



```python
plt.plot(df6)
plt.title('연도별 취업률 추이')
```

<pre>
Text(0.5, 1.0, '연도별 취업률 추이')
</pre>
<img src="data:image/png;base64,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"/>


```python
y = np.arange(4)
years = ['2020(2018.8~2019.2)', '2019(2017.8~2018.2)', '2018(2016.8~2017.2)','2017(2015.8~2016.2)']
values = [48.28, 50.08, 54.95, 52.65]
colors = ['y', 'dodgerblue', 'C2', 'r']
plt.xlabel('단위(%)')
plt.xlim([0, 100])

plt.barh(y, values, height=0.4, color = colors)
plt.yticks(y, years)

plt.show()
```

<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAcsAAAEGCAYAAAAKdL4tAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuNCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8QVMy6AAAACXBIWXMAAAsTAAALEwEAmpwYAAAZUklEQVR4nO3df7BfdZ3f8ecLwq8ISyIEF2EkiDQoSqdDCiJEfqzdpkiKtetgtYBWEVanYil1GevI2ixjXX4YZXQGpou4dgsV7I7Z2gU05ZdAA2HFRQR1lwLtAi4bIOVHNmvIu3+cE/nm5nvv5+ZK7vfG+3zM3PF7zvmcz4/DzXn5Oefc801VIUmSxrfTqDsgSdJMZ1hKktRgWEqS1GBYSpLUYFhKktRgWEqS1DBn1B3Qttt3331r4cKFo+6GJO1Q7r333r+pqgVT2dew3AEtXLiQNWvWjLobkrRDSfLoVPf1MqwkSQ2GpSRJDYalJEkNhqUkSQ2GpSRJDYalJEkNhqUkSQ2GpSRJDb6UYEd0772QjLoX0tT4hfPaATmzlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKmhGZZJ5iW5NsktSW5LcnCSRUlWJbkjycUDZRckuSjJ8n55z36/zT8PJ/l4v+3QJJcMq7/fPqk2+nWnJ/lRX8dNQ8ZwYl/36iSnT2LMRyS5KcntSb6RZNd+/bv6dauTnDZQ/o1Jrk+ydGDdfkn+OMmdSa6dxDHdJ8nXk+zc6p8kaZpV1YQ/wGuB1/af3wl8GfhTYGG/7jrg6P7zHwKfAf7jkHp2Am4E9uyX/wDYe1j9/edJtwH8a+DUCcZwW9/WLsAPgDTG/BZgt/7zxcB7gFcB3wN26z9/H9gdOAj4GnA1sHSgjq8Cb5nsMe0//yvgjNZ/kyO7d6D448+O+SONCLCmauLz63g/zZllVT1eVY/3i88AG4Ddq+qRft03gWP6smf0wTTMe4FvV9XzSfYANlXVuiH1v5Bkzja2Ma/fdzwv0oXlnsDz/UGbaMz3V9WGwT4BbwVWVdWGqnoBWA0cVlWPVtWZwOa+kmQ+sA/w7/uZ6Olj6t9qzP3na+mO01aSfCTJmiRrnpqo85KkV9yk71kmOQA4H7gUWDuwaS0wfxJVnEU3mwRYBDwwTv0rgAXb2MYc4Pf7YPrIkO2XAWuAHwJXDbR5SZKbk5yaZPckl4/p07HA4XQz4v2AwZyaqE+vB/4e8DHgN4Fzkuw/ttCYMVNVLwJzh1VYVVdW1eKqWrxgnEYlSdvHpMIyySl0lz7PAp6mm8ltNp8tQ2TY/kcD9/czMugC4cVh9fczrme3pY2qurCq3gr8Y+A9SQ4fqHs/4Fy6y6UHASf19yT3pgvZk4Gjge8A3+r3SZILgJPoLou+BKxjy3CcqE8bgdVVtbaq1tNdvn3DmGMydsySpBlqMg/4HAEsq6qzB07+u/WzIoB3A6sa1byP7r7jZk/S3bfbqn6AbW2jv2wLsB54Dhi8zLovsLGq1lfVRrrLngf2l4A/0a//VFUtqarv9vucAzxRVcv7oAS4G1iaZJckc4E3Aw+N06WfAIf3DzjtDCzu123u71ZjliTNXJP5iq6lwJIkt/TLjwHnAdcn2QCsrKoHG3W8Dfjk5oWqejjJYePV39+X3JY2PpfkqH48f1xVP+qXD6mqa5Lck+ROuhC9D7ih0d9lwLwkH+yXV1bVZUmuppslrgcu7MN3K1W1Psnv0QX8RuCKqvpZkg8Dd4035iSHMhCqkqSZIY1nXbZfw8m5wH1VdetIOjADJfkKsKKqJgzMxUmtmaY+Sa+4EZ1zpCT3VtXiqew7ypcSXE730Izo/vaSbgbrzFKSZpjJXIbdLqpqE1vex5zVqupZ2peHJUkj4OvuJElqMCwlSWowLCVJajAsJUlqGNkDPvolHHkkrPGPRyRpujizlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpYc6oO6Bt98DaB3jL194y6m5I28X9Z94/6i5IW3FmKUlSg2EpSVKDYSlJUoNhKUlSg2EpSVKDYSlJUoNhKUlSg2EpSVJDMyyTzEtybZJbktyW5OAki5KsSnJHkosHyi5IclGS5QPrDkxyQ5Lbk3xpYP2hSS4ZVn+/fVva2CnJiiR39eX3GTOGE/u6Vyc5fRJjPiLJTX2fv5Fk1379u/p1q5OcNlD+jUmuT7K0Xz6uH8/mn6eTHNE4pvsk+XqSnVv9kyRNr8nMLOcC51XVCcDngfOBFcCHqupYYGGSo/uylwIbgF0G9j8PuKSqlgCvTnJkv/4CYPk49bONbZwN/HlVHVNVx1bV2jFj+CywDDgOOD9JGmMuYFnf50eBU5O8qu/bO4CTgAuS7J7koH4sz/9i56rvVdUJ/Zj+JfDdqvrzgfq3GnPf55uB9zf6JkmaZs2wrKrHq+rxfvEZuqDavaoe6dd9EzimL3sGcNuYKp6jC8mdgL2AZ5LsAWyqqnVD6n8hyZxtbONkYFE/S7t4SBi+COwN7Ak8X1XVGPP9VbVhsE/AW4FVVbWhql4AVgOHVdWjVXUm8Mjw2vgMcNGY+rcac//5WuC9E/VNkjT9Jn3PMskBdDOrS4HBmdtaYP4Eu14BXAI8CKyrqoeBRcAD49S/AliwjW0cBVxfVW8H9gDePWb7ZcAa4IfAVQNtXpLk5iSn9rPEy8f06VjgcOBGYD/gqW3oE0leA+xfVT8YZ/vgmKmqF+lmncPKfiTJmiRrXnrupYmalSS9wiYVlklOoZshnQU8Dcwb2DyfLUNkrKuAY6tqEXBPko/SBcKLw+rvZ1zPbmMbT1bVPf3nbwNvGqh7P+Bc4KD+56T+nuTedC+SPxk4GvgO8K1+nyS5gO5y6xlV9RKwji3DsdUngA8AXx22YciYJ1RVV1bV4qpavPNe3taUpOk0mQd8jqC7f3d2Va2tqvXAbv2sCLpZ3KoJqtifLmABngAWAk8Crx1WP8AU2ngsyeav4TgBGLw/uC+wsarWV9VGusueB/aXgD/Rr/9UVS2pqu/2+5wDPFFVy/ugBLgbWJpklyRzgTcDD03QJ4BTgf8xduWwMUuSZq7JfEXXUmBJklv65cfoHtq5PskGYGVVPTjB/p8Gbkryc7rZ5Aeq6q+THDZe/f19yW1p43zgyv5W5Q+AlUmOAg6pqmuS3JPkTroHd+4DbmiMeRkwL8kH++WVVXVZkquB7wHrgQv78B0qyauBv6uqvx1Y92HgrvHGnORQ4CeNvkmSplkaz7psv4aTc4H7qurWkXRgBkryFWBFVU0YmHscvEe94XffME29kqaX32ep7SXJvVW1eCr7jvKlBJfTPTQjur+9pJvBOrOUpBlmMpdht4uq2gRcN6r2Z5qqepb25WFJ0gj4ujtJkhoMS0mSGgxLSZIaDEtJkhpG9oCPpu7wfQ5nzZlrRt0NSZo1nFlKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktRgWEqS1GBYSpLUYFhKktQwZ9Qd0La7/6/hoC+OuhfS1h49d9Q9kLYPZ5aSJDUYlpIkNRiWkiQ1GJaSJDUYlpIkNRiWkiQ1GJaSJDUYlpIkNTTDMsm8JNcmuSXJbUkOTrIoyaokdyS5eKDsgiQXJVk+sO6IJP8zyZ1Jvjiw/tAklwyrv98+qTaS7Nnvu/nn4SQfHzOGE/u6Vyc5fRJjPiLJTUluT/KNJLv269/Vr1ud5LSB8m9Mcn2SpZNpc5xjuk+SryfZudU/SdL0mszMci5wXlWdAHweOB9YAXyoqo4FFiY5ui97KbAB2GVg/y8AZ1bV24B9kpzUr78AWD5O/Uy2jap6vqpO6Pc/CfgpcNWYMXwWWAYcB5yfJI0xF7CsqpYAjwKnJnlV37d39O1ckGT3JAf1Y3l+G9rcasxVtRa4GXh/o2+SpGnWDMuqeryqHu8Xn6ELqt2r6pF+3TeBY/qyZwC3jaliblX9n/7znwD/MMkewKaqWjek/heSzNnGNjZ7L/DtqhobXC8CewN7As9XVTXGfH9VbRjsE/BWYFVVbaiqF4DVwGFV9WhVnQk8MqaacdscNub+87X9GCRJM8ik71kmOYBuZnUpsHZg01pg/gS7bkjypn5mdSLd+2gXAQ+MU/8KYME2trHZWcAfDFl/GbAG+CEDs87+MvDNSU7tZ4mXj+nTscDhwI3AfsBT29CnoW2OqX9wzFTVi3SzzmFlP5JkTZI1Lz3/1LAikqTtZFJhmeQU4DN0YfQ0MG9g83y2DJGxzqELjj+hm5U+QhcILw6rv59xPbuNbdBfpr2/n/UNrt8POBc4qP85qb8nuTddcJ8MHA18B/hWv0+SXEB3ufWMqnoJWMeW4Thun8Zrc0yZsWOeUFVdWVWLq2rxznsuaBWXJL2CJvOAzxF09+/Orqq1VbUe2K2fFQG8G1g13v5V9VBVLQXeAywEVgJPAq8dVn+/zza10XsfcN2Q9fsCG6tqfVVtpLvseWB/CfgT/fpPVdWSqvpuv885wBNVtbwPSoC7gaVJdkkyF3gz8NA4fRna5uaNw8YsSZq5JvMVXUuBJUlu6ZcfA84Drk+yAVhZVQ+Ot3OS84F/1i/+h6p6DnguyWHj1d/fl5x0G723AZ8caPco4JCquibJPUnupHtw5z7ghkZdy4B5ST7YL6+sqsuSXA18D1gPXNgH4Vaq6kfD2kzyYeCu8cac5FDgJ42+SZKmWRrPumy/hpNzgfuq6taRdGAGSvIVYEVVTRiYu71ucf36v10zTb2SJs/vs9RMluTeqlo8lX1H+VKCy+kemhHd317SzWCdWUrSDDOZy7DbRVVtYvg9xlmpqp6lfXlYkjQCvu5OkqQGw1KSpAbDUpKkBsNSkqSGkT3go6l7y36wxkf0JWnaOLOUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKlhzqg7oG333HP3csstGXU3NIudcEKNugvStHJmKUlSg2EpSVKDYSlJUoNhKUlSg2EpSVKDYSlJUoNhKUlSg2EpSVJDMyyTzEtybZJbktyW5OAki5KsSnJHkovHK9ev36psv/7QJJdMYb8FSS5Ksnxg3YFJbkhye5IvDRnDiX3dq5OcPokxH5Hkpr6+byTZtV//rn7d6iSnDZR/Y5LrkywdWHdaX/aesW2Oc0z3SfL1JDu3+idJml6TmVnOBc6rqhOAzwPnAyuAD1XVscDCJEePU45xygJcACyfwn6XAhuAXQb6eB5wSVUtAV6d5MgxY/gssAw4Djg/Sev1NwUs6+t7FDg1yav6vr0DOAm4IMnuSQ7qx/L85p2TzAc+BvwGcDzwb5L82kD9W425qtYCNwPvb/RNkjTNmmFZVY9X1eP94jN0QbV7VT3Sr/smcMyQci8kmTOsbJI9gE1VtW5b9uv7cwZw25huPkcXkjsBe/X1DHoR2BvYE3i+qiZ8V1dV3V9VGwb7BLwVWFVVG6rqBWA1cFhVPVpVZwKPDFTxBuD7VfV3VfViX/aNA/VvNeb+87XAeyfqmyRp+k36nmWSA+hmVpcCawc2rQXmDym3AlgwTtlFwAPj1D/RfuO5ArgEeBBYV1UPj9l+GbAG+CFw1UCblyS5Ocmp/Szx8jF9OhY4HLgR2A94apJ9+ku6/1Pwa/2M9CiGvId3zJjpg3XusAqTfCTJmiRr1q0bp1VJ0nYxqbBMcgrwGeAs4Glg3sDm+fQhMliunzk9O07ZuXSzva3qb+w3nquAY6tqEXBPko8O1L0fcC5wUP9zUn9Pcm+6ADsZOBr4DvCtfp8kuYDucusZVfUSsI4tw3HcPlXV08DvAf8d+E/A/2bLmeewMU+oqq6sqsVVtXjvvVulJUmvpMk84HME3f27s6tqbVWtB3brZ0UA7wZWjS0HMF5Z4EngtcPqb+w3nv3pQhzgCWDhwLZ9gY1Vtb6qNtJd9jywvwT8iX79p6pqSVV9t9/nHOCJqlreByXA3cDSJLskmQu8GXhovA5V1cqqejvwO3SXnP9qvGM6wbgkSTPAZL6iaymwJMkt/fJjdA/UXJ9kA7Cyqh5M8smx5fr7i1uVBUhy2Hj1T7TfOD4N3JTk53Qz1g8kOQo4pKqu6Z9IvZPuwZ37gBsaY14GzEvywX55ZVVdluRq4HvAeuDCPnyHSvJfgNfR3U/9WL/uw8Bd4405yaHATxp9kyRNszSeddl+DSfnAvdV1a0j6cAMlOQrwIqqmjAwFy1KXXHFNHVKGsLvs9SOKMm9VbV4KvuO8qUEl9M9NCO6v72km8E6s5SkGWYyl2G3i6raBFw3qvZnmqp6lvblYUnSCPi6O0mSGgxLSZIaDEtJkhoMS0mSGgxLSZIaRvY0rKZur72O5IQT1oy6G5I0azizlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKnBsJQkqcGwlCSpwbCUJKlhZF/+rKlL8hzw41H3Y4bYF/ibUXdihvBYvMxj8TKPxcsWVdVeU9nRN/jsmH481W/7/lWTZI3HouOxeJnH4mUei5clmfKrz7wMK0lSg2EpSVKDYbljunLUHZhBPBYv81i8zGPxMo/Fy6Z8LHzAR5KkBmeWkiQ1GJaSJDUYljuQJMuT3JrkjiSHj7o/0y3JvCTXJrklyW1JDk6yKMmq/phcPOo+Trckf5ZkqcchR/W/E3ck+eRsPh5Jzhs4T/yD2XQskixIclGS5f3y0LFP5Vzq31nuIJIsAV5TVccneTNwMXDyiLs13eYC51XV40neCZwPvB74UFU9kuS6JEdX1erRdnN6JPktYO9+cQWz9zjsAnwGOLWqnunX/Smz8HgkmQf8U+AE4BDgC3Tn+dlyLC4F/oLuXAFD/l0AuzKFc6kzyx3HbwLXAFTVD4FXj7Y706+qHq+qx/vFZ4ANwO5V9Ui/7pvAMaPo23RLshdwOvBHdCfDWXkcev8EeBS4pp9FHMXsPR4v0Z3Xd6V7c89TzKJjUVVnALcBJBnv38WUzqWG5Y5jP7pf/M02JpmV//2SHEA3q7wUWDuwaS0wfySdmn5fAn4P2ATsxew9DgCH0p3wTgE+BPxXZunxqKrn6MLiQWAl8FVm6bEAFjB87FM6l3oZdsexji1/yTdV1aZRdWZUkpwCLAPOAl4E5g1sns+W/wh+JSV5P/BYVd3TX45+lll4HAZsBG6qqo3AI0meZst/K7PmePS/D7vQXYKdTzebGjxPzJpjwfj/LvZgCufSWTkz2UHdDvwWQJI3Af93tN2ZfkmOAJZV1dlVtbaq1gO79TNNgHcDq0bXw2nzPuBNSa6l+534HeDwWXgcNruL7lIsSV4DPAfsOkuPx0HAz6r7A/r/R3fV4dWz8VhMcH6Y0rnUmeWO49vAyUlupzsZnD3i/ozCUmBJklv65ceA84Drk2wAVlbVg6Pq3HSpqndu/pzkd4H/RXeJaVYdh82q6u4kP05yB90s8zy6icBsPB5XA1cluRXYDbgCuI/ZeSxgyPkhyY+ZwrnUN/hIktTgZVhJkhoMS0mSGgxLSZIaDEtJkhoMS0lNSS5L8uuNMvv3b8+RfuX4pyOSfiHJ1XR/0L6hX/VXVXUm3Rty5vRl5gBf6cvNAb5RVV/ul98B3D3N3Za2O2eWksb6F1X1jv7nzCHbTwceqqrfoHth94lJXj+2UJJDk1zS/+/NSVYn+Uf9trcn+XcD5b68Hccj/dIMS0mT9dEkx9OdN54C6N8Us5bh55ILgOXAb9MF7PHAmUn2AM4BLuvr+CmwNsnbt/sIpCkyLCWNtXOSXZLskWR+kp379XcBDwNfB45L8tUkfwT8tKr+YrCCPhA3VdU6unf47gm8ii5YLwQ+V1UvDezyNWDYLFaaEbxnKWnQPXTf5vIS3avj1gOf7rd9H/gZ3Xdofpruhd1z6N6/+feB3QfqWQQ80H/+At03pADcBBwOnJTkNOD2qrqxqv4yySHbbVTSL8mwlPQLVfXlJP8NeKr/Fg8Akmz++DrgXLogPQz4OfBnwN8CPxmoai7djJKqWgv8dpLdgD8ErgQOqKovJvkacON2HZT0CjAsJY31ObqZ4y++jaGqPjCw/eMAST4AbKyq/9wvHzdQ5km6L9kd9Gng9+m+GWPzS6n37PfdlZefwJVmHO9ZSnrFVdXDdDNPAJIc2a+/l24m+f7+Wx9u6oscD9w63f2UJsuZpaRhruu/1mjQRVX1nW2o464kx1fVrX1I3gtQVS/Qfd3aoA/TPTUrzUh+RZek7SLJTsA/r6rrGuUWAvtX1V3T0jFpCgxLSZIavGcpSVKDYSlJUoNhKUlSg2EpSVKDYSlJUoNhKUlSw/8HLrMLPuz2rvEAAAAASUVORK5CYII="/>


```python
```
