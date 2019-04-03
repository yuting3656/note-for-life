onChange Real Example
======

~~~typeScript



  /**
   * 當狀態 @Input() 傳入內容異動時觸發
   */
  ngOnChanges(changes: SimpleChanges): void {
    // 偵測stateId 改變
    if (changes.stateId && changes.stateId.previousValue) {
      const prevVal = changes.stateId.previousValue;
      const curVal = changes.stateId.currentValue;
      if (prevVal !== curVal) {
        this.stateChanged(curVal);
      }
    }
  }

    // 在ngOnChanges 更變時候做偵測
  stateChanged(stateId: string) {
    this.currentDisplayOptions = this.stateMarketData[stateId];
    this.patchMarketData();
  }



~~~