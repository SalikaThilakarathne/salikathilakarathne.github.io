---
layout: page
title: use of neural nets for erosion prediction.
description: creating an artifical neural network
img:
importance: 2
category: work
---

Will soon be sharing an update on how I used a simple Artificial Neural Network (ANN) architecture to predict beach vulnerability.

***
This is how the sensitivity analysis was conducted to tune hyperparameters:

    ---
    def NN_reg_mod(layers,neurons, learning_rate,patience,dropout,batch):
    split_ratio_v = 0.90
    split_ratio_ts = 0.90

    temp_prof = all_storms
    learning_rate = learning_rate
        
    X, y = temp_prof.loc[:,['duration_H', 'surge_sum', 'wave_R',
                             'sl_initial', 'Hs_max']], temp_prof.loc[:,'beach_change':'beach_change']

    <>x_train, y_train = X[:int(len(X)*split_ratio_ts)], pd.DataFrame(y[:int(len(y)*split_ratio_ts)])
    <>x_test, y_test = X[int(len(X)*split_ratio_ts):], pd.DataFrame(y[int(len(y)*split_ratio_ts):])
    
    x_train, x_test,y_train,y_test = train_test_split(X,y,test_size = 0.2,random_state = 42)

    x_train_scaled, x_test_scaled = scale_datasets(x_train, x_test)

    es = EarlyStopping(monitor='val_loss', mode='min', verbose=1, patience=patience)


    <>Creating model using the Sequential in tensorflow
    model = Sequential()
    for i in np.arange(1, layers+1,1):
        model.add(Dense((neurons[i-1]), kernel_initializer='normal', activation='relu'))
        model.add(Dropout(dropout))
    Dense(1, kernel_initializer='normal', activation='linear')

    msle = MeanSquaredError()
    model.compile(loss=msle,optimizer=Adam(learning_rate=learning_rate),metrics=[msle])
    <>train the model
    history = model.fit(x_train_scaled.values,y_train.values,epochs=10000,batch_size=4,
                        validation_split=(1-split_ratio_v), verbose=0, callbacks=[es])
    train_accuracy = r2_score(y_train.beach_change,model.predict(x_train_scaled)[:,0].flatten())
    test_accuracy = r2_score(y_test.beach_change,model.predict(x_test_scaled)[:,0].flatten())

    return(train_accuracy,test_accuracy)
    ---



