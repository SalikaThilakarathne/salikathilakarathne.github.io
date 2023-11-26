---
layout: page
title: beach resilience to storm-induced erosion
description: what contributes to beach profile recovery after significant erosion events.
importance: 1
category: work
related_publications: thilakarathne_2023_machine
---

Currently working on this project. The beach recovery is checked in the 10-day post-storm period. A storm data set of 347 is used.

A lot of content to be updated, more work to be done. Following function was used to check the profile change during a storm event. This is a continuation from the susceptibility quantification approach.

    ---
    def prof_change_temp(start,end):
        start = pd.to_datetime(start)
        end= pd.to_datetime(end)
        
        start,end = (start - timedelta(5)).date(),(end + timedelta(5)).date()
        fig, ax = plt.subplots(figsize = (4,2.2), dpi = 300)
        x = np.arange(-115.0,386.0,5)
        temp = profile.loc[start:end,:'385']
        temp_wave = wave.resample('d').max().loc[start:end,'Hs_380']
        line, = ax.plot(x, gaussian_filter1d(temp.values[0], sigma=2), 
                        linewidth = 0.4, color = 'k')
        time_text = ax.text(-100, -4, '', bbox=dict(facecolor='green', alpha=0.1))
        time_text2 = ax.text(-100, -2.5, '', bbox=dict(facecolor='red', alpha=0.1))
    
        def animate(i):
            line.set_ydata(gaussian_filter1d(temp.values[i], sigma=2))  # update the data.
            time_text.set_text('date = {}'.format(temp.index[i].date()))
            time_text2.set_text('max Hs = {:.2f} m'.format(temp_wave[i]))
            return line, time_text,
    
        plt.grid(linewidth = 0.2)
        plt.axhline(y = 1.25, linewidth = 0.4, color = 'teal', label = 'HWL - 1.252 m')
        plt.xlabel('Cross-shore distance')
        plt.axvspan(0,150, alpha=0.1, color='r')
        plt.ylabel('Elevation (m)')
        plt.legend(frameon = True)
    
        ani = animation.FuncAnimation(
            fig, animate,frames = len(temp), interval=750, blit=True)
        plt.close(ani._fig)
        #Call function to display the animation
        return HTML(ani.to_html5_video())
    ---

