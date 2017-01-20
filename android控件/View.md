#判断控件是否可以上滑的代码
```
/**
 * @return Whether it is possible for the child view of this layout to
 *         scroll up. Override this if the child view is a custom view.
 */
public boolean canChildScrollUp() {
    if (android.os.Build.VERSION.SDK_INT < 14) {
        if (mTarget instanceof AbsListView) {
            final AbsListView absListView = (AbsListView) mTarget;
            return absListView.getChildCount() > 0
                    && (absListView.getFirstVisiblePosition() > 0 || absListView.getChildAt(0)
                            .getTop() < absListView.getPaddingTop());
        } else {
            return ViewCompat.canScrollVertically(mTarget, -1) || mTarget.getScrollY() > 0;
        }
    } else {
        return ViewCompat.canScrollVertically(mTarget, -1);
    }
}
```
